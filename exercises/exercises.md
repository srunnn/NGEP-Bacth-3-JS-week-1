NOTE: to remove git: use `Remove-Item -Recurse -Force .git`
How to change repository when cloning from someone else?
-	git remote -v                       (you will see other repository)
-	git remote remove origin 
-	git remote -v                       (you should see nothing)
-	git remote add origin <URL>

# Week 1 Lab : Git Command Checklist

Do these **in order**. Check each box as you complete it. Ask your trainer if a step fails.

# Part A : First commit 

- `git init` : turn the folder containing `greeting.js` into a Git repository.
- `git status` : read the output. What does it say about `greeting.js`?
- `git add greeting.js` : stage the file.
- `git status` again : what changed in the output?
- `git commit -m "initial commit: add greeting.js"`
- `git status` : confirm it says "nothing to commit, working tree clean".

# Part B : Track changes 

- Open `greeting.js` and add a second `console.log()` line with your name.
- `git status` : notice the file is listed as "modified".
- `git add greeting.js`
- `git commit -m "add personalized greeting"`

# Part C : Connect to GitHub 

- On GitHub, create an empty repo and copy its HTTPS URL.
- `git remote add origin <url>`
- `git branch -M main`
- `git push -u origin main`
- Refresh GitHub in your browser : confirm your commits appear.

# Part D : Practice pull

- On GitHub's website, edit `greeting.js` directly (add a comment) and commit the
      change there.
- Back in your terminal: `git pull`
- Confirm your local file now has the change you made on GitHub.

# Part E : Make a mistake, then fix it with reset

- Add a line to `greeting.js` that intentionally breaks the code, e.g. `console.log(`
      with no closing parenthesis.
- `git add greeting.js && git commit -m "oops: broken syntax"`
- Run `node greeting.js` : confirm it errors out.
- `git log --oneline` : copy the commit hash from **before** the broken commit.
- `git reset --hard <that-commit-hash>` : go back to the working version.
- Run `node greeting.js` again : confirm it works.
- `git log --oneline` : confirm the broken commit is gone.


# Part F : Simulate teamwork (15 min, pair up if possible)

- Add one more feature to `greeting.js` (e.g. a function `sayGoodbye()` that logs a
      farewell message and call it).
- `git add . && git commit -m "add sayGoodbye function"`
- `git push`
- Swap screens with a classmate (or re-clone your own repo into a new folder) and run
      `git clone <url>` to prove the repo is fully reproducible from GitHub.

# Wrap-up (5 min)

- `git log --oneline` : you should see **4+ commits**.
- Confirm the repo on GitHub matches your local `main` branch (`git status` should say
      "up to date with origin/main").
