# Changelog

## [v2.3.0] – 2021-12-17
  - Syntaxes: refactored Surface/HEEx/EEx with many improvements (thanks to @deathaxe).
  - Themes: slightly darken the embed punctuation markers for Surface and (H)EEx tags.
  - Elixir: allow digits in sigil string modifiers.
  - Preferences: index Elixir `@attribute` definitions for "Goto Definition".

## [v2.2.0] – 2021-09-18
  - Syntax: added support for the [HEEx](https://hexdocs.pm/phoenix_live_view/Phoenix.LiveView.Helpers.html#sigil_H/2) template syntax inside the `~H` sigil.
  - Syntax: added support for the [Surface](https://surface-ui.org/template_syntax) template syntax inside the `~F` sigil.
  - Elixir: match the `**` power operator.
  - HTML (EEx): switched to version 2 and removed usage of `with_prototype`.
  - SQL: match the `;` token; fixed the `/**/` comment scope.
  - Themes: highlight interpolated Elixir with a lighter background.
  - Themes: don't italicize the sigil type.

## [v2.1.0] – 2021-07-25

- Elixir: disabled highlighting Elixir code within Markdown comments. Reasons:
  * Not completely reliable.
  * Not all Elixir code was recognized.
  * Can be distracting.
  * Probably affects speed.
  + If you'd like to re-enable this feature, override the package and uncomment the relevant lines.
- Elixir: added `meta.type.elixir` scope to specs and types.
- Elixir: added `meta.doc.elixir` scope to doc attributes.
- Elixir: highlight an atom with a function call as a module constant: `:lists.sort([])`
- Elixir: recognize a record's name as an entity symbol for "Goto Definition".
- Elixir: recognize `record` as a special keyword in type declarations:\
  `@type t :: record(:user, name: binary, age: integer)`
- Elixir: fix: stop highlighting params after `when` in free-form functions: `def a + b when a == 0 and b == 0`
- Elixir: fixed lambda calls in capture expressions: `&fun.(&1, &2)`
- Elixir: consider a line continuation backslash to be the start of an argument list:
  ```elixir
  with \
    {:ok, _} <- newline do
  end
  ```
- Elixir: allow `unquote` and `unquote_splicing` to have arguments without parentheses.
- Elixir: match `.:` as an atom keyword.
- Elixir: `^^` is not an operator.
- Themes: don't italicize parameters in Monokai.
- Themes: completely italicize types and specs, except for `::`, `|` and strings.
- SQL: highlight `WITH ORDINALITY` and `AT TIME ZONE`.
- Builds: removed `$` from the file names so they're correctly displayed in the menu.

## [v2.0.5] – 2021-05-30

- Elixir: also highlight `catch`, `else`, `after` clauses in function do-end blocks.
- Elixir: use own scopes for `after` and `rescue` keywords.
- Elixir: allow commas inside item access brackets, e.g.: `%{}[a: 1, b: 2]`
- Elixir: fixed: some multi-line when-type clauses were not matched correctly.
- Elixir: don't match `def func()` as a type after writing a `|` in a type spec.
- Elixir: use greedy matching for identifiers and atoms as well.
- Elixir: the `meta.mapping.elixir` scope wasn't set correctly for maps.
- SQL: fixed escapes breaking strings, e.g.: `fragment("? = '\"string\"'::jsonb", x)`

## [v2.0.4] – 2021-05-17

- Elixir: use greedy matching for module names.

## [v2.0.3] – 2021-05-13

- Elixir: moved syntax and color-scheme files into sub-folders.
- Elixir: highlight EEx tags inside comments.

## [v2.0.2] – 2021-05-05

- Elixir: fixed a bug where a comma was seen as invalid, such as in `if a == nil, ...`.
- SQL: added decimal number highlighting.
- SQL: added general function-call syntax matching.
- SQL: removed `support.function.psql` scope to simplify the file.

## [v2.0.1] – 2021-05-02

- Elixir: fixed a bug affecting, for example, multi-line `with` statements.
- Elixir: fixed captures such as `&MyApp.User |> f(&1)`.
- Elixir: fixed matching iex continuation lines (`...>`) in markdown comments.
- SQL: highlight `BY` as a standalone keyword.

## [v2.0.0] – 2021-04-27

The Elixir syntax definition has been reworked amounting to a complete rewrite
bringing among other things the following features and improvements:

- Type highlighting in `@spec`, `@type`, `@typep`, `@opaque`, `@callback` and `@macrocallback`.
- Parameter highlighting (also in `fn`, `case`, `with`, `for`, `try` and `receive`).
- Function call highlighting (e.g. `inspect error`, `Enum.map(...)`).
- Highlight `as: A` argument in alias/require statements.
- Better matching for `def`/`defmodule`/etc. statements.
- Highlight quoted member variables/functions (e.g. `:erlang."=/="(1, 2)`).
- Fixes to strings, numerics, escapes, captures etc.
- Newest Elixir operators and functions.
- Highlight LiveView, YAML and JSON strings.
- Syntax definition for EEx in Elixir, e.g.: `defmodule <%= @module %>.View do end`
- Some keywords are variables depending on the context (e.g. `def = 0`).
- Markdown highlighting within `@doc` comments and also Elixir code examples.
- Highlight SQL (e.g. jsonb operators) inside the Ecto `fragment()` function but also inside `sql("INSERT INTO ...")`.
- Git merge conflicts are highlighted.
- Added Monokai and Mariana theme color scheme rules.
- Correct scope for symbol names for the "Goto Definition" command.
- Speed optimizations: rules and regexps are ordered in such a way
  that they match the most likely occurring tokens first.
- Snippets for `|> IO.inspect(label: "...")`, `|> then()` and `|> tap()`.
- Extensive test-suite containing countless checks to ensure quality and avoid regressions.
- Fixed Github CI syntax tests job.

## [v1.7.0] – 2020-05-20

Thanks @dkarter
- Allow leex file to be picked up

## [v1.6.0] – 2019-11-20

Thanks to @azizk again
- We now have regex syntax highlighting
- EEx syntax highlighting now reuses html definition and interpolates Elixir parts into it
- various fixes on general Elixir syntax definition
- comprehensive sublime syntax tests

## [v1.3.0] – 2019-03-22

Thanks to @azizk
- Also apply syntax to files with elixirc and iex in hashbang
- Module names can only have ASCII letters, fixed regex to do that
- Highlight module names as normal atoms when found in map/kwlist keys
- Highlight unicode identifers for atoms, variables and function names

## [v1.2.0] – 2019-02-13

- Add Comment so we don't need https://github.com/elixir-editors/elixir-tmbundle alongside

## [v1.1.3] – 2019-02-01

- Fix binary `^^^` highlight
- Highlight more operators

## [v1.1.0] – 2017-12-13

- Add HTML (EEX)
