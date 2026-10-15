# Contributing to MindCast_GM

This guide explains how to get the code, make changes, and submit them for review.

## Branches

| Branch | Purpose |
|--------|---------|
| `main` | Stable, reviewed code. Maintainers only merge here. |
| `research` | Experimental and in-progress work. Contributor PRs target this branch. |

**Never push directly to `main` or `research`.** All changes go through a pull request.

## 1. Clone the repository

```bash
git clone https://github.com/salcore/MindCast_GM.git
cd MindCast_GM
```

(Using SSH? `git clone git@github.com:salcore/MindCast_GM.git`)

**External contributors:** you won't have write access, so first **fork** the repo on GitHub, clone your fork, and add the original as `upstream`:

```bash
git remote add upstream https://github.com/salcore/MindCast_GM.git
```

Then use `upstream` instead of `origin` when pulling the latest `research`, and push your branches to `origin` (your fork).

## 2. Set up your environment

Never commit your virtual environment. `.mindcast/` is listed in `.gitignore`.

```bash
python -m venv .mindcast
source .mindcast/bin/activate        # Windows: .mindcast\Scripts\activate
pip install -r requirements.txt
```

## 3. Create a feature branch

Always branch off the latest `research`:

```bash
git checkout research
git pull origin research
git checkout -b <type>/<short-description>
```

Branch naming: `feature/...`, `fix/...`, `docs/...`, `experiment/...`
Example: `feature/add-eval-script`

## 4. Make your changes

- Keep changes focused: one feature or fix per branch.
- Add or update tests where applicable.
- Do not commit datasets, model weights, secrets, or `.env` files.

## 5. Commit your work

```bash
git add <files>
git commit -m "Add evaluation script for baseline model"
```

Commit message tips:
- Use the imperative mood ("Add", "Fix", "Update").
- Keep the first line under ~70 characters.
- Make small, logical commits.

## 6. Push your branch

```bash
git push origin <type>/<short-description>
```

## 7. Open a pull request

1. Go to the repository on GitHub and click **Compare & pull request**.
2. Set the **base branch to `research`** and compare it with your branch.
3. Write a clear title and description covering:
   - **What** you changed
   - **Why** you changed it
   - **How** to test it
4. Request a review from a teammate or maintainer.

### Pull request checklist

- [ ] Branch is up to date with `research`
- [ ] Code runs and tests pass
- [ ] No secrets, large files, or virtual environments committed
- [ ] Description explains the change clearly

## 8. Review and merge

- At least one approval is required before merging.
- Address feedback by pushing more commits to the same branch. The PR updates automatically.
- A maintainer merges the PR once approved.
- After merging, delete your branch. Start your next contribution from step 3 with a fresh branch.

## Keeping your branch up to date

If `research` has moved ahead while your PR is open:

```bash
git fetch origin
git rebase origin/research     # or: git merge origin/research
```

If you rebased a branch you already pushed, update it with:

```bash
git push --force-with-lease origin <type>/<short-description>
```

## Promoting to `main`

Only maintainers open and merge `research` → `main`, once the work is validated.

## Questions?

Open an issue or ask in the team channel.