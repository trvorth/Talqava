# Contributing to Talqava

Thank you for helping. Talqava is an open-source (MIT) way to run an organization with AI agents, made for business owners who are not technical. Every contribution should keep that person in mind: plain words, one obvious action, nothing they have to understand about the code.

By taking part you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Ways to help

- **Report a problem.** Open an [issue](https://github.com/Talqava/Talqava/issues/new/choose) with what you did, what you expected and what happened. Screenshots help.
- **Suggest an idea.** Open an issue describing the problem you want solved, before the solution.
- **Add a marketplace role or team.** A role is one YAML file in [`marketplace/`](marketplace/); a team is an entry in [`marketplace/teams.yaml`](marketplace/teams.yaml). These need no TypeScript.
- **Improve the wording.** If a label, message or page confused you, that is a bug. Suggest plainer words.
- **Write code.** Pick an issue, say in it that you are working on it, then open a pull request.
- **Security problems** are never reported in public issues. See [SECURITY.md](SECURITY.md).

## Set up

You need [Node.js](https://nodejs.org) 22.18 or newer and [git](https://git-scm.com).

```bash
git clone https://github.com/Talqava/Talqava.git
```

```bash
cd Talqava
```

```bash
npm install
```

```bash
npm start
```

Open <http://localhost:8787>. Your data goes in `data/`, which git ignores. Talqava is TypeScript run directly by Node, so there is no build step: change a file and restart.

To work on the Mac app, see [The desktop app](README.md#the-desktop-app) in the readme.

## Before you open a pull request

```bash
npm run check
```

This type-checks the code and runs every test. It must pass. The tests use stand-ins for AI models and for GitHub, so they need no key and cost nothing.

Every pull request and every push to `main` also runs `npm ci` and `npm run check` automatically in GitHub Actions (see [`.github/workflows/check.yml`](.github/workflows/check.yml)). A pull request shows the check at the bottom of its page; it must be green before merge.

- **Add or change a test** for what you changed. Tests live in `test/core` and `test/local`, and describe behaviour in a sentence (`test("a group stops at its monthly budget …")`).
- **Keep pull requests small**: one change, explained. Say what it does for the person using the app, and how you checked it.
- **Never commit secrets** (API keys, tokens, passwords) or anything from your `data/` folder. The repository is public.
- If your change shows on screen, check it in both the light and dark themes and add a screenshot to the pull request.

## How we write code

- **Follow the [brand guide](docs/brand/README.md)** for the logo, colours, type and voice.
- **Plain language in the app.** "Agents", "tasks", "groups", "reports to"; no jargon the owner has to learn. Errors say what happened and what to do next.
- **Comments explain why**, in full sentences. Names say what.
- **The page is plain JavaScript** (`public/app.js`) with a tiny `h()` helper for elements. No framework.
- **Styles use the named theme colours** (`--text`, `--panel`, `--accent-ink`, `--warn`, `--bad` and so on, in `public/theme.css`), never a fixed colour, so both themes keep working.
- **Agents ask before acting.** Anything that changes files, spends money or sends something waits for the owner's approval unless the owner chose otherwise. Do not add a way around that.
- **No new dependency** without a good reason, said in the pull request, and a licence our [open-source policy](legal/OPEN_SOURCE_POLICY.md) allows. Run `npm run licenses` after any dependency change and commit the notices it updates.

## Ideas, but not code, from elsewhere

We study other projects for ideas. We never copy another project's code, designs or wording into Talqava unless its licence allows it and the pull request says so.

## Licence

By contributing, you agree that your contribution is licensed under the [MIT License](LICENSE), the same as the rest of Talqava.
