---
layout: post
title: How I Restored My Git Contributions
author: Rajan Joshi
twitter: https://twitter.com/razanjoshi
website: 
github: https://github.com/razanjoshi
---

# Restoring Your Git Contributions

I was a software engineer for my previous company for 4 years. We were a Ruby on Rails-based platform where we had been working for throughout the years. So every commit you push to your GitHub repo, be it private or public creates a mark in your profile’s contribution chart. The darker the shade, the higher the number of commits you pushed.
We know we may or may not have roasted each other looking at each other’s contribution chart on our GitHub profile, making statements about who has coded more in the past months or years. As a software engineer’s life cycle continues, he/she moves on from his/her current job to a new one, which means we change organizations throughout our journey. The different organization has their own private repositories(repos) and access controls, which means you can only access their repos through these private work (email) accounts associated with it. After you leave the company, it seems all your commits are scrapped off as they archive those stale email addresses of their ex-employees.
So here are few tips to help you import those contributions to your profile:

- **Add the work email address to the account**
Add your work email as secondary emails in your GitHub profile’s email settings.

- **Show private contributions**
Thanks to GitHub, make sure you have chosen the private contributions option in order to show all the contributions you have made to a private repo on GitHub. This will only show the index on the chart and one can not trace the contributions made to a private repo.

- **Importing contributions from GitHub Enterprise, GitLab, BitBucket to GitHub.**
This is a bit tricky as if you work in different version control from the GitHub. For this, we can use a Python script which will import all the commits you(and only you) have pushed to those accounts. Go through the given link below so you can have a better understanding.

**How it works:**

- Clone the repo
```
git clone git@github.com:miromannino/Contributions-Importer-For-Github.git
```
- Make sure you create a blank repo or use an existing blank repo which is authored by your profile in which you want to import your contributions. This will be your Mock Repo
- Make sure those two repos are inside a common directory/folder. i.e. Mock repo & the repo given above.
- Go to the cloned repo and create a file at the root directory.

run_script.py [name of the file]

    import git
    from git_contributions_importer import *
    # Your private repo or Bitbucket repo
    repo = git.Repo("path/to/your/private/repo")
    # Your mock repo
    mock_repo = git.Repo("path/to/your/mock/repo")
    importer = Importer([repo], mock_repo)
    # I use both my personal email and work email here,
    # Since the private repo uses work email, and Github profiles 
    uses
    # my work email
    importer.set_author(['rajan.joshi@personalemail.com', 
    'rajan.joshi@workemail.co.uk'])
    importer.import_repository()

Run `python3 run_script.py`
Go to your Mock Repo in your terminal and push the changes. [If you don’t do this, you will not see changes in your chart]

If you're still confused refer my original blog at:
[https://medium.com/@razan.joc/how-i-restored-my-git-contributions-7ddb27f06d4e](https://medium.com/@razan.joc/how-i-restored-my-git-contributions-7ddb27f06d4e)