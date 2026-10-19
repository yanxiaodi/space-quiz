# Copilot instructions

## Project structure and running

The app is a standalone space quiz in `index.html`, with semantic HTML, inline CSS, and inline vanilla JavaScript. Keep the app self-contained: it runs by opening `index.html` in a browser and has no build step or runtime dependencies. The workspace `.mcp.json` configures Playwright MCP for browser interaction checks.

The page has three screens inside `<main>`: intro, quiz, and results. `showScreen()` switches them using the `hidden` attribute. Quiz content lives in the `questions` array; `renderQuestion()` builds the radio options, while form submission checks an answer, updates progress and feedback, advances the quiz, and eventually shows the results screen.

## Quiz conventions

- Each question has `category`, `text`, `options`, `answer`, and `explanation` fields. `answer` is the zero-based index of the correct item in `options`; the explanation is shown after checking the answer.
- Use `questions.length` for quiz counts and progress. If the question count changes, also update the intro copy that says “Ten questions” and “10 questions.”
- Keep screen IDs and their JavaScript references in sync when changing the page structure. Focus is moved to the question or results heading when the screen changes.
- Answers use native radio inputs inside a fieldset and legend. Keep status feedback announced with the existing live region and retain keyboard operation.
- Theme colors are CSS custom properties in `:root`, with dark-mode values in `@media (prefers-color-scheme: dark)`. Reduced-motion CSS is defined in `@media (prefers-reduced-motion: reduce)`; JavaScript-driven motion should check that preference as well.
