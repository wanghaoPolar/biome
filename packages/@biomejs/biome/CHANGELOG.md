# @biomejs/biome

## 2.0.0

### Major Changes

- [#4823](https://github.com/biomejs/biome/pull/4823) [`d3b7b2d`](https://github.com/biomejs/biome/commit/d3b7b2d734a3cb40b7e75c65d9e04b1a7f30f2fb) Thanks [@ematipico](https://github.com/ematipico)! - Biome now resolves globs and paths from the configuration. Before, paths and globs were resolved from the working directory.

- [#4803](https://github.com/biomejs/biome/pull/4803) [`f86999d`](https://github.com/biomejs/biome/commit/f86999d6a0a52c78e6f09a19bf353253bc1bbe72) Thanks [@ematipico](https://github.com/ematipico)! - The Biome formatter doesn't add a trailing command in `.json` files, even when `json.formatter.trailingCommas` is set to `true`.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`72ef826`](https://github.com/biomejs/biome/commit/72ef8260135e9d15fe34429846a1b81e940c7efe) Thanks [@ematipico](https://github.com/ematipico)! - Reduced accepted values for formatter options:

  - The option `--quote-style` doesn't accept `Single` and `Double` anymore.
  - The option `--quote-properties` doesn't accept `AsNeeded` and `Preserve` anymore.
  - The option `--semicolons` doesn't accept `AsNeeded` and `Always` anymore.
  - The option `--arrow-parenthesis` doesn't accept `AsNeeded` and `Always` anymore.
  - The option `--trailing-commas` doesn't accept `ES5`, `All` and `None` anymore.
  - The option `--attribute-position` doesn't accept `Single` and `Multiline` anymore.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`17ff3f6`](https://github.com/biomejs/biome/commit/17ff3f63e74e5916a102efd1c709a68e98383487) Thanks [@ematipico](https://github.com/ematipico)! - Remove `BIOME_LOG_DIR`.

  The environment variable `BIOME_LOG_DIR` isn't supported anymore.

  Use `BIOME_LOG_PATH` instead.

- [#4766](https://github.com/biomejs/biome/pull/4766) [`1907096`](https://github.com/biomejs/biome/commit/190709672495d3adda58473ad73e411b3273c02a) Thanks [@ematipico](https://github.com/ematipico)! - Remove deprecated rules.

  The following _deprecated_ rules have been deleted:

  - `noInvalidNewBuiltin`
  - `noNewSymbol`
  - `useShorthandArrayType`
  - `useSingleCaseStatement`
  - `noConsoleLog`

  Run the command `biome migrate --write` to update the configuration.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`1be9494`](https://github.com/biomejs/biome/commit/1be949465b1127712ec1dc89771c265bfb3b4631) Thanks [@ematipico](https://github.com/ematipico)! - Remove `indentSize` deprecated option.

  The deprecated option `indentSize`, and its relative CLI options, has been removed:

  - Configuration file: `formatter.indentSize`
  - Configuration file: `javascript.formatter.indentSize`
  - Configuration file: `json.formatter.indentSize`
  - CLI option `--indent-size`
  - CLI option `--javascript-formatter-indent-size`
  - CLI option `--json-formatter-indent-size`

  Use `indentWidth` and its relative CLI options instead.

- [#4853](https://github.com/biomejs/biome/pull/4853) [`dac3882`](https://github.com/biomejs/biome/commit/dac388281e06e7fc33134abc088bd1ac968e8e2e) Thanks [@SuperchupuDev](https://github.com/SuperchupuDev)! - Remove `ROME_BINARY`. Use `BIOME_BINARY` instead.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`0680ba5`](https://github.com/biomejs/biome/commit/0680ba51765fbb3d6334008471485f9ed54791d3) Thanks [@ematipico](https://github.com/ematipico)! - Remove support for legacy suppressions.

  Biome used to support "legacy suppressions" that looked like this:

  ```js
  // biome-ignore lint(complexity/useWhile): reason
  ```

  This format is no longer supported.

- [#4894](https://github.com/biomejs/biome/pull/4894) [`d43aa7e`](https://github.com/biomejs/biome/commit/d43aa7efa7ef2d91c06e103b93beac54dcedd0e4) Thanks [@ematipico](https://github.com/ematipico)! - Remove support for `max_line_length` from `.editorconfig`, as it isn't part of the official spec anymore.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`36b4b1c`](https://github.com/biomejs/biome/commit/36b4b1cfbe483ecef0c32d06c87aeb75c0cae0f4) Thanks [@ematipico](https://github.com/ematipico)! - Remove support for `rome-ignore` suppression comment.

  Use the `biome-ignore` suppression comment instead.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`36b4b1c`](https://github.com/biomejs/biome/commit/36b4b1cfbe483ecef0c32d06c87aeb75c0cae0f4) Thanks [@ematipico](https://github.com/ematipico)! - Remove support for `rome.json`.

- [#4664](https://github.com/biomejs/biome/pull/4664) [`55acffe`](https://github.com/biomejs/biome/commit/55acffeb18256763f5bf6fbb20f2bafd23e4765f) Thanks [@ematipico](https://github.com/ematipico)! - Remove the option `all` from the linter.

  The options `linter.rules.all` and `linter.rules.<group>.all` has been removed.

  The number of rules in Biome have increased in scope and use cases, and sometimes some of them can conflict with each other.

  The option was useful at the beginning, but now it's deemed harmful, because it can unexpected behaviours in users projects.

  To automatically remove it, run the following command:

  ```shell
  biome migrate --write
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`1accca5`](https://github.com/biomejs/biome/commit/1accca58a651398df0ca1719d32c4d537459c0eb) Thanks [@ematipico](https://github.com/ematipico)! - Removed the option `trailingComma` from the configuration and the CLI. Use the option `trailingCommas` instead:

  ```diff
  {
    "javascript": {
      "formatter": {
  -      "trailingComma": "es5"
  +      "trailingCommas": "es5"
      }
    }
  }
  ```

  ```diff
  -biome format --trailing-comma=es5
  +biome format --trailing-commas=es5
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`0425b90`](https://github.com/biomejs/biome/commit/0425b903077d97bbc5aff497f64a6fa3931caef3) Thanks [@ematipico](https://github.com/ematipico)! - Removed `--apply` and `--apply-unsafe`.

  The CLI options `--apply` and `--apply-unasfe` aren't accepted anymore. Use `--write` and `--write --unafe` instead:

  ```diff
  -biome check --apply-unsafe
  +biome check --write --unsafe
  ```

  ```diff
  -biome check --apply
  +biome check --write
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`6a8ad85`](https://github.com/biomejs/biome/commit/6a8ad85aa520dc3d59dd085255df79b6bc3c848c) Thanks [@ematipico](https://github.com/ematipico)! - Removed support for `assert` syntax.

  Biome now longer supports the `assert` syntax, use the new `with` syntax instead

  ```diff
  -import {test} from "foo.json" assert { for: "for" }
  -export * from "mod" assert { type: "json" }
  +import {test} from "foo.json" with { for: "for" }
  +export * from "mod" with { type: "json" }
  ```

- [#4651](https://github.com/biomejs/biome/pull/4651) [`d8f91ba`](https://github.com/biomejs/biome/commit/d8f91bae07d828cb6e6f4c3fa714505c709d1159) Thanks [@arendjr](https://github.com/arendjr)! - The rule `useImportRestrictions` has been renamed to `noPackagePrivateImports`.

  To avoid confusion with `noRestrictedImports`, `useImportRestrictions` has been
  renamed to `noPackagePrivateImports`.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`3936022`](https://github.com/biomejs/biome/commit/39360226f674cecd0fbdbe63f23fab9ad98193e4) Thanks [@ematipico](https://github.com/ematipico)! - Previously, files that should exceed the configured size limit would throw an error, and the CLI would exit with an error code.

  Now, the CLI ignores the file, emits a _information_ diagnostic and doesn't exit with an error code.

- [#4730](https://github.com/biomejs/biome/pull/4730) [`a478377`](https://github.com/biomejs/biome/commit/a478377129491ee20acd5e122228994a062b8b00) Thanks [@ematipico](https://github.com/ematipico)! - The `style` rules aren't recommended anymore.

  Linting rules that belong to the group `style` aren't recommended anymore. Here's the list of rules that aren't recommended anymore:

  - `useNumberNamespace`
  - `noNonnullAssertion`
  - `useAsConstAssertion`
  - `noParameterAssign`
  - `noInferrableTypes`
  - `useNodejsImportProtocol`
  - `useExportType`
  - `useDefaultParameterLast`
  - `noUnusedTemplateLiteral`
  - `useExponentiationOperator`
  - `useEnumInitializers`
  - `useShorthandFunctionType`
  - `useLiteralEnumMembers`
  - `noVar`
  - `noUselessElse`
  - `useNumericLiterals`
  - `noCommaOperator`
  - `useConst`
  - `noArguments`
  - `useSelfClosingElements`
  - `useImportType`
  - `useTemplate`
  - `useSingleVarDeclarator`
  - `useWhile`

  Use `biome migrate` to enable these rules, to avoid breaking changes.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`0680ba5`](https://github.com/biomejs/biome/commit/0680ba51765fbb3d6334008471485f9ed54791d3) Thanks [@ematipico](https://github.com/ematipico)! - Remove the code action `quickfix.suppressRule`.

  The code action `quickfix.suppressRule` was removed in favour of two new code actions:

  - `quickfix.suppressRule.inline.biome`: a code action that adds a suppression comment for each violation.
  - `quickfix.suppressRule.topLevel.biome`: a code action that adds a suppression comment at the top of the file which suppresses a rule for the whole file.

  Given the following code

  ```js
  let foo = "one";
  debugger;
  ```

  The code action `quickfix.suppressRule.inline.biome` will result in the following code:

  ```js
  // biome-ignore lint/style/useConst: <explanation>
  let foo = "one";
  // biome-ignore lint/suspicious/noDebugger: <explanation>
  debugger;
  ```

  The code action `quickfix.suppressRule.topLevel.biome`, instead, will result in the following code:

  ```js
  /** biome-ignore lint/suspicious/noDebugger: <explanation> */
  /** biome-ignore lint/style/useConst: <explanation> */

  let foo = "one";
  debugger;
  ```

- [#4819](https://github.com/biomejs/biome/pull/4819) [`78c8910`](https://github.com/biomejs/biome/commit/78c8910ff0eb63288618e744fd64529682b87d46) Thanks [@ematipico](https://github.com/ematipico)! - Changed default formatting of `package.json`.

  When Biome encounters a file called `package.json`, by default it will format the file with all objects and arrays expanded.

  ```diff
  - { "name": "project", "dependencies": { "foo": "latest" } }
  + {
  +  "projectName": "project",
  +  "dependencies": {
  +    "foo": "^1.0.0"
  +  }
  + }
  ```

- [#4788](https://github.com/biomejs/biome/pull/4788) [`93d1e23`](https://github.com/biomejs/biome/commit/93d1e232ec38e30f71929e61c8fa6c0bcb9e6d03) Thanks [@ematipico](https://github.com/ematipico)! - The `organizeImports` is now part of Biome Assist

- [#4766](https://github.com/biomejs/biome/pull/4766) [`1907096`](https://github.com/biomejs/biome/commit/190709672495d3adda58473ad73e411b3273c02a) Thanks [@ematipico](https://github.com/ematipico)! - The rule `noConsoleLog` has been removed

- [#4759](https://github.com/biomejs/biome/pull/4759) [`9568041`](https://github.com/biomejs/biome/commit/95680416c9c7aec57635e2e5762db3163d693414) Thanks [@ematipico](https://github.com/ematipico)! - The rule `noVar` now belongs to the `suspicious` group

- [#4760](https://github.com/biomejs/biome/pull/4760) [`74eaf89`](https://github.com/biomejs/biome/commit/74eaf89bcd5cbec9c4207b5f2b87e150decb471f) Thanks [@ematipico](https://github.com/ematipico)! - The rule `useExhaustiveDependencies` is not recommended anymore. If your codebase uses `react` and relies on that rule, you have to enable it:

  ```jsonc
  // biome.json
  {
    "linter": {
      "rules": {
        "correctness": {
          "useExhaustiveDependencies": "error",
        },
      },
    },
  }
  ```

- [#4777](https://github.com/biomejs/biome/pull/4777) [`4f4cafb`](https://github.com/biomejs/biome/commit/4f4cafb16d8c05a545190feda2acb44a217eac88) Thanks [@ematipico](https://github.com/ematipico)! - The rule `useWhile` now belongs to the `complexity` group

- [#4935](https://github.com/biomejs/biome/pull/4935) [`112d43e`](https://github.com/biomejs/biome/commit/112d43ecac2120d70576bd9879b6005e28badae4) Thanks [@fireairforce](https://github.com/fireairforce)! - The rule `lint/a11y/useAltText` doesn't check the element's attributes containing object spread.

  The following code doesn't trigger the rule anymore:

  ```jsx
  <img src="test.png" alt={alt} {...restProps}></img>
  ```

- [#4945](https://github.com/biomejs/biome/pull/4945) [`069cbb4`](https://github.com/biomejs/biome/commit/069cbb4f6118e5daf6113bbe54ec3c4c3e4b7d0f) Thanks [@Conaclos](https://github.com/Conaclos)! - Prior to Biome 2.0, non-ASCII names were accepted by default.
  They are now rejected.

  For example, the following code is now reported as invalid by the `useNamingConvention` rule.

  ```js
  let johnCafé;
  ```

  If you want to allow non ASCII filenames and non-ASCII identifiers, you need to set the `requireAscii` options in your Biome configuration file to `false`:

  ```json
  {
      "linter": {
          "rules": {
              "style": {
                  "useFilenamingConvention": {
                      "level": "on",
                      "options": {
                          "requireAscii": false
                      }
                  }
                  "useFilenamingConvention": {
                      "level": "on",
                      "options": {
                          "requireAscii": false
                      }
                  }
              }
          }
      }
  }
  ```

### Minor Changes

- [#4718](https://github.com/biomejs/biome/pull/4718) [`21ef4aa`](https://github.com/biomejs/biome/commit/21ef4aa7a1a6bd4701a8d2eae38c14c456c7c5bc) Thanks [@ematipico](https://github.com/ematipico)! - Add new option `javascript.parser.jsxEverywhere`. This new option allows to control whether Biome should expect JSX syntax in `.js`/`.ts` files.

  When `jsxEverywhere` is set to `false`, having JSX syntax like `<div></div>` inside `.js`/`.ts` files will result in a **parsing error**.

  This option defaults to `true`.

- [#4911](https://github.com/biomejs/biome/pull/4911) [`d400d69`](https://github.com/biomejs/biome/commit/d400d69bbf91339dc3931bad6f0648e75da19019) Thanks [@kaykdm](https://github.com/kaykdm)! - Add the new rule [`noFloatingPromises`](https://biomejs.dev/linter/rules/no-floating-promises).

- [#4948](https://github.com/biomejs/biome/pull/4948) [`b8c57d2`](https://github.com/biomejs/biome/commit/b8c57d2724bda65a27575a741a70df5600f5c6a4) Thanks [@arendjr](https://github.com/arendjr)! - Add the new rule [`noImportCycles`](https://biomejs.dev/linter/rules/no-import-cycles).

- [#4650](https://github.com/biomejs/biome/pull/4650) [`c1b2e7b`](https://github.com/biomejs/biome/commit/c1b2e7b74023c822e625c6e5a55c5f40c33aa2ca) Thanks [@ematipico](https://github.com/ematipico)! - Add the new rule [`noTsIgnore`](https://biomejs.dev/linter/rules/no-ts-ignore).

- [#4731](https://github.com/biomejs/biome/pull/4731) [`5c3e3e1`](https://github.com/biomejs/biome/commit/5c3e3e1516055f3577c51e5b0e503710b2684de2) Thanks [@unvalley](https://github.com/unvalley)! - Add the new rule [`noUnwantedPolyfillio`](https://biomejs.dev/linter/rules/no-unwanted-polyfillio).

- [#4819](https://github.com/biomejs/biome/pull/4819) [`78c8910`](https://github.com/biomejs/biome/commit/78c8910ff0eb63288618e744fd64529682b87d46) Thanks [@ematipico](https://github.com/ematipico)! - Added a JSON format option `expand`. The option `json.formatter.expand` allows to enforce the formatting of arrays and objects on multiple lines, regardless of their length.

- [#4867](https://github.com/biomejs/biome/pull/4867) [`94bf15e`](https://github.com/biomejs/biome/commit/94bf15e3d24ddae0631aa2e9966a7ade771356d1) Thanks [@ematipico](https://github.com/ematipico)! - Linter groups now accept new options to enable/disable all rules that belong to a group, and control the severity
  of the rules that belong to those groups.

  For example, you can downgrade the severity of rules that belong to `"style"` to emit `"info"` diagnostics:

  ```json
  {
    "linter": {
      "rules": {
        "style": "info"
      }
    }
  }
  ```

  You can also enable all rules that belong to a group using the default severity of the rule using the `"on"` option:

  ```json
  {
    "linter": {
      "rules": {
        "complexity": "on"
      }
    }
  }
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`f281e8a`](https://github.com/biomejs/biome/commit/f281e8aadcdf9eb25e45def923c3c153c9ff299c) Thanks [@ematipico](https://github.com/ematipico)! - Biome assist is a new feature of the Biome analyzer. The assist is meant to provide **actions**. Actions differ from linter rules in that they aren't meant to signal errors.

  The assist will provide code actions that users can opt into via configuration or via IDEs/editors, using the Language Server Protocol.

  The assist **is enabled by default**. However, you can turn if off via configuration:

  ```json
  {
    "assist": {
      "enabled": false
    }
  }
  ```

  You can turn on the actions that you want to use in your configuration. For example, you can enable the `useSortedKeys` action like this:

  ```json
  {
    "assist": {
      "actions": {
        "source": {
          "useSortedKeys": "on"
        }
      }
    }
  }
  ```

  Alternatively, IDE/editor users can decide which action to apply on save _directly from the editor settings_, as long as the assist is enabled.

  For example, in VS Code you can apply the `useSortedKeys` action when saving a file by adding the following snippet in `settings.json`:

  ```json
  {
    "editor.codeActionsOnSave": {
      "source.biome.useSortedKeys": "explicit"
    }
  }
  ```

  In Zed, you can achieve the same by adding the following snippet in `~/.config/zed/settings.json`:

  ```json
  {
    "code_actions_on_format": {
      "source.biome.useSortedKeys": true
    }
  }
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`59f7e10`](https://github.com/biomejs/biome/commit/59f7e100aca357d322d331713668bf6c38c5603d) Thanks [@ematipico](https://github.com/ematipico)! - Biome migrate eslint outputs a better overriding behavior.

  A Biome rule can have multiple ESLint equivalent rules.
  For example, [useLiteralKeys](https://biomejs.dev/linter/rules/use-literal-keys/) has two ESLint equivalent rules: [dot-notation](https://eslint.org/docs/latest/rules/dot-notation) and [@typescript-eslint/dot-notation](https://typescript-eslint.io/rules/dot-notation/).

  Previously, Biome wouldn't always enable a Biome rule even if one of its equivalent rules was enabled.
  Now Biome uses the higher severity level of all the equivalent ESLint rules to set the severity level of the Biome rule.

  The following ESLint configuration...

  ```json
  {
    "rules": {
      "@typescript-eslint/dot-notation": "error",
      "dot-notation": "off"
    }
  }
  ```

  ...is now migrated to...

  ```json
  {
    "linter": {
      "rules": {
        "complexity": {
          "useLiteralKeys": "error"
        }
      }
    }
  }
  ```

  ...because `error` is higher than `off`.

- [#5076](https://github.com/biomejs/biome/pull/5076) [`279311a`](https://github.com/biomejs/biome/commit/279311a213e71f1b5f7dca5c04459076065ef47e) Thanks [@siketyan](https://github.com/siketyan)! - Add a new lint rule `noConstantBinaryExpression`.
  This rule is inspired from ESLint's [no-constant-binary-expression](https://eslint.org/docs/latest/rules/no-constant-binary-expression) rule.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `noUnusedImports` now reports empty named imports and suggests its removal ([#3574](https://github.com/biomejs/biome/issues/3574)).

  The rule now suggests the removal of empty named imports such as:

  ```diff
  - import {} from "mod";
  ```

- [#4760](https://github.com/biomejs/biome/pull/4760) [`f281e8a`](https://github.com/biomejs/biome/commit/f281e8aadcdf9eb25e45def923c3c153c9ff299c) Thanks [@ematipico](https://github.com/ematipico)! - Biome users can now configure code actions from linter rules as well as assist actions directly in the settings of their IDE/editor.

  For example, let's consider the lint rule [`noSwitchDeclarations`](https://biomejs.dev/linter/rules/no-switch-declarations/), which has an unsafe fix.
  Previously, if you wanted to use this rule, you were "forced" to enable it via configuration, and if you wanted to apply its fix when you saved a file, you were forced to mark the fix as safe:

  ```json
  {
    "linter": {
      "rules": {
        "correctness": {
          "noSwitchDeclarations": {
            "level": "error",
            "fix": "safe"
          }
        }
      }
    }
  }
  ```

  Now, you can benefit from the code action without making the fix safe for the entire project. IDEs and editors that are LSP compatible allow to list a series of "filters" or code actions that can be applied on save. In the case of VS Code, you will need to add the following snippet in the `settings.json`:

  ```json
  {
    "editor.codeActionsOnSave": {
      "quickfix.biome.correctness.noSwitchDeclarations": "explicit"
    }
  }
  ```

  Upon save, Biome will inform the editor the apply the code action of the rule `noSwitchDeclarations`.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `noUnusedImports` now keeps comments separated from the import with a blank line ([#3401](https://github.com/biomejs/biome/issues/3401)).

  Here is an example:

  ```diff
    // Orphan comment

  - // Header comment
  - import {} from "mod";
  ```

- [#5083](https://github.com/biomejs/biome/pull/5083) [`7aa79e7`](https://github.com/biomejs/biome/commit/7aa79e79268fd5450dc791838e91812c59220ca2) Thanks [@siketyan](https://github.com/siketyan)! - Formatter option `bracketSpacing` is now also supported in JSON files.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `useValidTypeof` now accepts comparisons with variables.

  Previously, the rule required to compare a `typeof` expression against another `typeof` expression or a valid string literal.
  We now accept more cases, notably comparison against a variable:

  ```js
  if (typeof foo === bar) {
    // ...
  }
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! -

- [#4730](https://github.com/biomejs/biome/pull/4730) [`a478377`](https://github.com/biomejs/biome/commit/a478377129491ee20acd5e122228994a062b8b00) Thanks [@ematipico](https://github.com/ematipico)! - You can now enable lint rules using the default severity suggested by Biome using the new variant `"on"`, when enabling a rule.

  For example, the default severity of the rule `style.noVar` is `error`, so you would use `"on"`, and then linting a code that uses `var`, will result in an error:

  ```json
  {
    "linter": {
      "recommended": false,
      "rules": {
        "style": {
          "noVar": "on"
        }
      }
    }
  }
  ```

  ```js
  // main.js
  var name = "tobias";
  ```

  The command `biome lint main.js` will result in an error due to the default severity assigned to `noVar`.

  Refer to the documentation page of each rule to know their suggested diagnostic severity, or use the command `biome explain <RULE_NAME>`:

  ```shell
  biome explain noVar
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noUnknownProperty](https://biomejs.dev/linter/rules/no-unknown-property/) now accepts more known CSS properties ([#4549](https://github.com/biomejs/biome/issues/4549)).

  ```diff
  - ['anchor-default', 'anchor-scroll', 'inset-area', 'position-animation', 'position-fallback', 'position-fallback-bounds', 'position-try-options']
  + ['anchor-scope', 'interpolate-size', 'line-fit-edge', 'masonry', 'masonry-auto-tracks', 'masonry-direction', 'masonry-fill', 'masonry-flow', 'masonry-slack', 'masonry-template-areas', 'masonry-template-tracks', 'position-anchor', 'position-area', 'position-try-fallbacks', 'position-visibility', 'scroll-start-target', 'text-box', 'view-transition-class', 'view-transition-group']
  ```

  This change replaces deprecated properties, improving CSS validation.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`9a5280e`](https://github.com/biomejs/biome/commit/9a5280e39a7dce19568a77600c31942530a0d080) Thanks [@ematipico](https://github.com/ematipico)! - Introduce a new option `objectWrap` for JS formatter.
  It does the same thing as Prettier's [Object Wrap](https://prettier.io/docs/options#object-wrap) option.

  For example, the following code is considered as already formatted when `objectWrap` is `preserve` (default):

  ```js
  const obj = {
    foo: "bar",
  };
  ```

  However, when `objectWrap` is `collapse`, it will be formatted to the following output:

  ```js
  const obj = { foo: "bar" };
  ```

- [#4899](https://github.com/biomejs/biome/pull/4899) [`c047886`](https://github.com/biomejs/biome/commit/c04788665ee45cd4416f4f8ee88fe865ba3b1791) Thanks [@Conaclos](https://github.com/Conaclos)! - Introduce `includes`.

  Biome allows users to `include` and `ignore` files in its configuration using glob patterns.

  For example, in the following configuration, all files of the `src/` directory are checked except the ones ending with the extension `.test.js`.

  ```json
  {
    "files": {
      "include": ["src/**"],
      "ignore": ["**/*.test.js"]
    }
  }
  ```

  Some Biome users have requested the ability to ignore a set of files except some of the files.
  With the current system, this is not possible because `include` is always applied before `ignore`.

  Also, many Biome users [reported](https://github.com/biomejs/biome/issues/2421) [issues](https://github.com/biomejs/biome/issues/3345) with the behavior of the glob patterns.
  Notably:

  - `src/**` is interpreted as `**/src/**`
  - `*.js` is interpreted as `**/*.js`

  To solve all these issues, we introduce a new field `includes`, which replaces both `include` and `ignore`.
  `includes` accepts an array of glob patterns with a stricter and more intuitive behavior than the previous glob pattern format.
  A glob starting with a `!` is an exception.
  This replaces `ignore` patterns.

  The previous configuration must be updated as follows:

  ```json
  {
    "files": {
      "includes": ["src/**", "!**/*.test.js"]
    }
  }
  ```

  You can run `biome migrate` to automatically convert from `include` and `ignore` to `includes`.

- [#4713](https://github.com/biomejs/biome/pull/4713) [`0a9d85a`](https://github.com/biomejs/biome/commit/0a9d85af5f9b35e6db78ae49236dac04e03faeb0) Thanks [@ematipico](https://github.com/ematipico)! - Introduce the `domains` linter feature. The Biome linter now has a new way to opt-in rules, with a concept called `domains`.

  Domains can be seen as concepts shared by different rules.

  You can enable and disable multiple rules that belong to a domain. When you assign `"all"`, Biome will enable all the rules, when you assign `"none"`, Biome will disable the rules, when you assign "recommended", Biome will enable all rules of the domain that are recommended.

  ```json5
  // biome.jsonc
  {
    linter: {
      domains: {
        test: "all", // all rules that belong to this domain are enabled
        react: "recommended", // only the recommended rules from this domain are enabled
        solid: "none", // rules related to Solid are disabled
      },
    },
  }
  ```

  New domains introduced:

  - `test`: it will enable rules:
    - `noExportsInTest`
    - `noExcessiveNestedTestSuites`
    - `noDuplicateTestHooks`
    - `noFocusedTests`
      And it will inject the following globals:
    - `after`
    - `afterAll`
    - `afterEach`
    - `before`
    - `beforeEach`
    - `beforeAll`
    - `describe`
    - `it`
    - `expect`
    - `test`
  - `next`: it will enable rules for Next.js projects:
    - `useExhaustiveDependencies`
    - `useHookAtTopLevel`
    - `noImgElement`
    - `noHeadImportInDocument`
    - `noHeadImportInDocument`
  - `react`: it will enable rules for React projects:
    - `useExhaustiveDependencies`
    - `useHookAtTopLevel`
  - `solid`: it will enable rules for Solid projects:
    - `noReactSpecificProps`

  For more information regarding how Biome enables rules via domains, please refer to the documentation page of each rule.

- [#4760](https://github.com/biomejs/biome/pull/4760) [`0680ba5`](https://github.com/biomejs/biome/commit/0680ba51765fbb3d6334008471485f9ed54791d3) Thanks [@ematipico](https://github.com/ematipico)! - The Biome analyzer now supports a new top-level suppression. These suppression have to be placed at the top of the file, and they must be followed by two newlines (`\n\n\`).

  The analyzer rules specified inside the block comment will be suppressed for the whole file.

  In the example, we suppress the rules `lint/style/useConst` and `lint/suspicious/noDebugger` for the whole file:

  ```js
  // main.js
  /**
   * biome-ignore-all lint/style/useConst: i like let
   * biome-ignore-all lint/suspicious/noDebugger: needed now
   */

  let path = "/path";
  let _tmp = undefined;
  debugger;
  ```

  In this other example, we suppress `lint/suspicious/noEmptyBlock` for a whole CSS file:

  ```css
  /**
  /* biome-ignore-all lint/suspicious/noEmptyBlock: it's fine to have empty blocks
  */

  a {
  }
  span {
  }
  ```

  A new diagnostic is emitted if `biome-ignore-all` suppression isn't placed at the top of the file:

  ```block
  file.js:3:1 suppressions/incorrect ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

    ! Top level suppressions can only be used at the beginning of the file.

      2 │ let foo = 2;
    > 3 │ /**
        │ ^^^
    > 4 │ * biome-ignore-all lint/style/useConst: reason
    > 5 │ */
        │ ^^
      6 │ let bar = 33;

    i Rename this to biome-ignore

      2 │ let foo = 2;
      3 │ /**
    > 4 │ * biome-ignore-all lint/style/useConst: reason
        │   ^^^^^^^^^^^^^^^^
      5 │ */
      6 │ let bar = 33;


  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `useExportType` and `useImportType` now ignore TypeScript declaration files ([#4416](https://github.com/biomejs/biome/pull/4416)).

- [#4760](https://github.com/biomejs/biome/pull/4760) [`d469189`](https://github.com/biomejs/biome/commit/d469189298a2358989ee7e906b840f1d30fe5ad5) Thanks [@ematipico](https://github.com/ematipico)! - The package now requires `v2` of the WebAssembly packages. The internal APIs of Workspace are now `camelCase`.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [useArrayLiterals](https://biomejs.dev/linter/rules/use-array-literals/) now provides a code fix.

  ```diff
  - const xs = new Array();
  + const xs = [];
  ```

  The code fix is currently marked as unsafe.
  We plan to make it safe in a future release of Biome.

### Patch Changes

- [#5014](https://github.com/biomejs/biome/pull/5014) [`028af9c`](https://github.com/biomejs/biome/commit/028af9c89af4ac62089907e5523584bef47639f9) Thanks [@vohoanglong0107](https://github.com/vohoanglong0107)! - Fix [#5001](https://github.com/biomejs/biome/issues/5001), where the CSS formatter removes whitespace from selector preceded by a comment

- [#4949](https://github.com/biomejs/biome/pull/4949) [`7b91d19`](https://github.com/biomejs/biome/commit/7b91d19383c1e1ce9395f7c2049b8fbc353f2965) Thanks [@ematipico](https://github.com/ematipico)! - Biome logs a warning in case a folder contains `biome.json` and `biome.jsonc`, and it will use `biome.json` by default.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noUndeclaredVariables](https://biomejs.dev/linter/rules/no-undeclared-variables/) is now able to bind read of value to a type-only import in ambient contexts ([#4526](https://github.com/biomejs/biome/issues/4526)).

  In the following code, `A` is now correctly bound to the type-only import.
  Previously, `A` was reported as an undeclared variable.

  ```ts
  import type { A } from "mod";

  declare class B extends A {}
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4317](https://github.com/biomejs/biome/issues/4317), setter parameter can contain a trailing comma, the following example will now parsed correctly:

  ```ts
  export class DummyClass {
    set input(value: string) {}
  }
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4575](https://github.com/biomejs/biome/issues/4575), don't wrap selector indentation after css comments.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4258](https://github.com/biomejs/biome/issues/4258), where fixed css parse error with @-moz-document url-prefix().

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Don't parse the files that don't end with the json extension as JSON files in the `.vscode` directory ([#4391](https://github.com/biomejs/biome/issues/4391))

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `biome migrate eslint` now correctly resolves scoped package named `eslint-config` with a path.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#3836](https://github.com/biomejs/biome/issues/3836), css parser allow multiple semicolons after a declaration, the following example will now parsed correctly:

  ```css
  .foo {
    color: red;
  }
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4553](https://github.com/biomejs/biome/issues/4553), `noUselessFragments` fix result has invalid syntax for JSX attribute, the follow code will fix:

  ```jsx
  <Suspense
    fallback={
      <>
        <span>Loading...</span>
      </>
    }
  >
    {children}
  </Suspense>
  ```

  it will fix as:

  ```jsx
  <Suspense fallback={<span>Loading...</span>}>{children}</Suspense>
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `biome migrate eslint` now correctly handles shared ESLint configuration that don't follow the ESLint naming convention ([#4528](https://github.com/biomejs/biome/issues/4528)).

  ESLint recommends that a package that exports a shared configuration be prefixed with `eslint-config-` or simply named `eslint-config`.
  This is only a recommendation.
  Packages that export shared configurations can have arbitrary names.
  Biome is now able to load any package.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4756](https://github.com/biomejs/biome/issues/4756), `noDuplicateProperties` now throws lint errors properly when we use `@supports`.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - `biome migrate eslint` now correctly handles ESLint configuration with `null` values in file lists ([#4740](https://github.com/biomejs/biome/issues/4740)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4202](https://github.com/biomejs/biome/issues/4202), where the formatting of the test function was different from prettier.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#342](https://github.com/biomejs/biome/issues/342), js parser handle unterminated `JSX_STRING_LITERAL` properly

  ```jsx
  function Comp() {
    return (
        <a rel="
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix CSS parser case error, `@-moz-document url-prefix(https://example.com)` and `@-moz-document domain(example.com)` are now valid.

- [#5043](https://github.com/biomejs/biome/pull/5043) [`3868597`](https://github.com/biomejs/biome/commit/386859758287739ff00e7b0d9faa53ab9adb62af) Thanks [@Jayllyz](https://github.com/Jayllyz)! - Fix [#5024](https://github.com/biomejs/biome/issues/5024), add `useJsxKeyInIterable` rule to React domain.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noUnusedVariables](https://biomejs.dev/linter/rules/no-unused-variables/) no longer reports top-level variables in a global declaration file as unused.

- [#4903](https://github.com/biomejs/biome/pull/4903) [`2a80687`](https://github.com/biomejs/biome/commit/2a8068733fa1fbffea4043d56123f00f2ddb8a35) Thanks [@fireairforce](https://github.com/fireairforce)! - Export Named Type support `default` parser.

  The following code is now parsed successfully:

  ```ts
  export { type A as default } from "./b.ts";
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [useNamingConvention](https://biomejs.dev/linter/rules/use-naming-convention/) no longer suggests renaming top-level variables in a global declaration file.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4413](https://github.com/biomejs/biome/issues/4413), where the GraphQL formatter adds a new line at the start of block comments on Windows.

- [#4964](https://github.com/biomejs/biome/pull/4964) [`e750523`](https://github.com/biomejs/biome/commit/e750523d5b96e828246edd2945c3c09cff0de49b) Thanks [@siketyan](https://github.com/siketyan)! - Fix #1597, useExhaustiveDependencies now consider React hooks stable within parentheses or type assertions.

- [#4944](https://github.com/biomejs/biome/pull/4944) [`66823f7`](https://github.com/biomejs/biome/commit/66823f78f83b082aa982f2d1dfdef2ab0ed84d20) Thanks [@ematipico](https://github.com/ematipico)! - Fix a bug where `--config-path` accepted configuration files with unsupported extensions. Now only `.json` and `.jsonc` are accepted, and an error is raised otherwise.

- [#4882](https://github.com/biomejs/biome/pull/4882) [`7f0e969`](https://github.com/biomejs/biome/commit/7f0e96903ef4a4a58ab672a9b929544c7761a744) Thanks [@fireairforce](https://github.com/fireairforce)! - Fix [#4751](https://github.com/biomejs/biome/issues/4751) by checking fragments inside `JSXElement` and conditional expressions. For example:

  The Case:

  ```jsx
  <section>
    <>
      <div />
      <div />
    </>
  </section>
  ```

  And:

  ```jsx
  showFullName ? <>{fullName}</> : <>{firstName}</>;
  ```

  It will report.

- [#4863](https://github.com/biomejs/biome/pull/4863) [`846e4a4`](https://github.com/biomejs/biome/commit/846e4a4be6eb1f62c8b5baf52f98f8c1c39bdb9e) Thanks [@arendjr](https://github.com/arendjr)! - The rule `noFallthroughSwitchCase` no longer panics on some incomplete code snippets.

- [#5008](https://github.com/biomejs/biome/pull/5008) [`99f27a2`](https://github.com/biomejs/biome/commit/99f27a2b31fc15825a3175d342e2403e9764d22c) Thanks [@bushuai](https://github.com/bushuai)! - Fix [#5007](https://github.com/biomejs/biome/issues/5007) `noMissingVarFunction` false positives for `container-name`.

- [#4901](https://github.com/biomejs/biome/pull/4901) [`ba26e90`](https://github.com/biomejs/biome/commit/ba26e9003862a0ee4c202634729a5c70da1f6a31) Thanks [@bushuai](https://github.com/bushuai)! - Fix [#4841](https://github.com/biomejs/biome/issues/4841), shebang and top leading comments in cjs files are now handled correctly

  - shebang only (keep it as is)

  ```
  #!/usr/bin/env node
  ```

  - comments only (keep it as is)

  ```
  // comment
  ```

  - with shebang

  ```diff
  - #!/usr/bin/env node"use strict";
  + #!/usr/bin/env node
  + "use strict";
  let some_variable = "some value";
  ```

  - with comment

  ```diff
  - // comment
  - "use strict"; // comment
  + "use strict";
  + // comment
  let some_variable = "some value";
  ```

  - with shebang and comment

  ```diff
  - #!/usr/bin/env node"use strict";
  - // comment
  + #!/usr/bin/env node
  + "use strict";
  + // comment
  let some_variable = "some value";
  ```

- [#4714](https://github.com/biomejs/biome/pull/4714) [`e3ec2e2`](https://github.com/biomejs/biome/commit/e3ec2e2cf494bc72d9097624dc610b5c984d5bd6) Thanks [@fireairforce](https://github.com/fireairforce)! - Suppression comment should not fail with inner comments in functions.

  The following code:

  ```ts
  // biome-ignore lint/complexity/useArrowFunction: not work
  const foo0 = function (bar: string) {
    // biome-ignore lint/style/noParameterAssign: work
    bar = "baz";
  };
  ```

  The suppression comment `// biome-ignore lint/style/noParameterAssign: work` will not be invalid.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noMisleadingCharacterClass](https://biomejs.dev/linter/rules/no-misleading-character-class/) no longer panics on malformed escape sequences that end with a multi-byte character ([#4587](https://github.com/biomejs/biome/issues/4587)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4121](https://github.com/biomejs/biome/issues/4326), don't ident a CSS selector when has leading comments.

- [#5099](https://github.com/biomejs/biome/pull/5099) [`9280cba`](https://github.com/biomejs/biome/commit/9280cbacbf429a4ab074e8890e6f7b1a85ae8e01) Thanks [@fireairforce](https://github.com/fireairforce)! - Fix [#4982](https://github.com/biomejs/biome/issues/4982), the JavaScript parser now throws a syntax error for the following code:

  ```ts
  type T = import;
  type U = typeof import;
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#342](https://github.com/biomejs/biome/issues/342), js parser is no longer progressing for an invalid object member name:

  ```js
  ({
    params: { [paramName: string]: number } = {}
  })
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4334](https://github.com/biomejs/biome/issues/4334), don't insert trailing comma on type import statement.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noUnusedImports](https://biomejs.dev/linter/rules/no-unused-imports/) no longer reports used values imported as types in an external module ([#3895])(https://github.com/biomejs/biome/issues/3895).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#342](https://github.com/biomejs/biome/issues/342), "expected a declaration as guaranteed by is_at_ts_declare_statement" error for declare interface:

  ```ts
  declare;
  interface;
  ```

- [#5052](https://github.com/biomejs/biome/pull/5052) [`1099147`](https://github.com/biomejs/biome/commit/109914706b4eed535e4c6aab4968f0cf46940f82) Thanks [@ah-yu](https://github.com/ah-yu)! - Fix [#5031](https://github.com/biomejs/biome/issues/5031). Improve CSS formatting for numbers:

  ```diff
  .class {
  -	padding: .5em;
  -	marding: 1.0;
  +	padding: 0.5em;
  +	marding: 1;
  }
  ```

- [#5066](https://github.com/biomejs/biome/pull/5066) [`56527db`](https://github.com/biomejs/biome/commit/56527db372a56a9c20df7a67bc9663667a7d32ae) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#5053](https://github.com/biomejs/biome/issues/5053), now the rule correctly handles `console.log` inside arrow function expressions.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#3229](https://github.com/biomejs/biome/issues/3229), where Biome wasn't idempotent when block comments were placed inside compound selectors.

- [#4998](https://github.com/biomejs/biome/pull/4998) [`f0e6521`](https://github.com/biomejs/biome/commit/f0e65211457ec71df17b041976665032079a2e03) Thanks [@mehm8128](https://github.com/mehm8128)! - Mark `useSelfClosingElements` as safe and improve error message.

- [#5023](https://github.com/biomejs/biome/pull/5023) [`4d0a797`](https://github.com/biomejs/biome/commit/4d0a79769e50596ce3ebae76469a55307c2aca43) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4875](https://github.com/biomejs/biome/issues/4875), where the Jetbrains IDE terminal would output not clickable, relative file path link to the diagnostic file. This does not fix paths without line and column numbers.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4719](https://github.com/biomejs/biome/issues/4719), `bracketSameLine` now performs as expected when a comment is placed before the last JSX attribute.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Don't panic when a multi-byte character is found in a unicode escape sequence ([#4564](https://github.com/biomejs/biome/issues/4564)).

- [#5085](https://github.com/biomejs/biome/pull/5085) [`65c5b7a`](https://github.com/biomejs/biome/commit/65c5b7a18d33f7e42f8c4a97bc7e95e710a8f341) Thanks [@siketyan](https://github.com/siketyan)! - Fix [#4947](https://github.com/biomejs/biome/issues/4947): the `useTemplate` lint rule now ignores concatenated literals folded to multiple lines.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix a panic related to bogus import statements in `useExhaustiveDependencies` ([#4568](https://github.com/biomejs/biome/issues/4568)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4026](https://github.com/biomejs/biome/issues/4026), don't move comments in `grid-template`.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix `useSortedClasses` false positive and Supplementary test case ([#3394](https://github.com/biomejs/biome/issues/3394)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Don't panic when a declare statement is followed by an unexpected token.([#4562](https://github.com/biomejs/biome/issues/4562)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noLabelWithoutControl](https://biomejs.dev/linter/rules/no-label-without-control/) detects button tags as input ([#4511])(https://github.com/biomejs/biome/issues/4511).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Add `RegExpStringIterator` to the analyzer globals.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noUselessFragments](https://biomejs.dev/linter/rules/no-useless-fragments/) now handles `JsxAttributeInitializerClause`, ensuring that fragments inside expressions like `<A b=<></> />` are preserved. ([#4208](https://github.com/biomejs/biome/issues/4208)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4533](https://github.com/biomejs/biome/issues/4533), don't throw error when pseudo class after a webkit scrollbar pseudo element.

  The following code will not report:

  ```css
  ::-webkit-scrollbar-thumb:hover {
  }
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - Fix [#4323](https://github.com/biomejs/biome/issues/4258), where `lint/a11y/useSemanticElement` accidentally showed recommendations for `role="searchbox"` instead of `role="search"`.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [noControlCharactersInRegex](https://biomejs.dev/linter/rules/no-control-characters-in-regex) no longer panics when it encounters an unterminated unicode escape sequence ([#4565](https://github.com/biomejs/biome/issues/4565)).

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [useArrayLiterals](https://biomejs.dev/linter/rules/use-array-literals/) now reports all expressions using the `Array` constructors.

  Previously, the rule reported only use of the `Array` constructor in expressions statements.

  ```js
  // This was reported
  new Array();
  // This was not reported
  const xs = new Array();
  ```

- [#4771](https://github.com/biomejs/biome/pull/4771) [`8d1062f`](https://github.com/biomejs/biome/commit/8d1062f45562df441acc8fc59e460c3f814e5f45) Thanks [@dyc3](https://github.com/dyc3)! - `tsconfig.*.json` files will now be treated the same as `tsconfig.json` files.

- [#4955](https://github.com/biomejs/biome/pull/4955) [`0bf4eaa`](https://github.com/biomejs/biome/commit/0bf4eaa83ba79710687d1f57c05b31f30e43538e) Thanks [@Conaclos](https://github.com/Conaclos)! - The `useNamingConvention` rule now suggests a rename that preserves uppercase if possible.

  For instance, Biome suggested renaming `HTMLWrapper` as `htmlWrapper`:

  ```diff
  - import HTMLWrapper from "HTMLWrapper.tsx";
  + import htmlWrapper from "HTMLWrapper.tsx";

    function component() {
  -   return <HTMLWrapper> </HTMLWrapper>;
  +   return <htmlWrapper> </HTMLWrapper>;
    }
  ```

  Since both `PascalCase` and `CamelCase` are accepted, Biome now suggests renaming `HTMLWrapper` as `HtmlWrapper`:

  ```diff
  - import HTMLWrapper from "HTMLWrapper.tsx";
  + import HtmlWrapper from "HTMLWrapper.tsx";

    function component() {
  -   return <HTMLWrapper> </HTMLWrapper>;
  +   return <HtmlWrapper> </HTMLWrapper>;
    }
  ```

- [#5067](https://github.com/biomejs/biome/pull/5067) [`7243cce`](https://github.com/biomejs/biome/commit/7243cce87617988a09527c09e7296238e79de8ed) Thanks [@dyc3](https://github.com/dyc3)! - Fix Biome being unable to parse `insert_final_newline = unset` in EditorConfig files.

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [useArrowFunction](https://biomejs.dev/linter/rules/use-arrow-function/) now preserves directives ([#4530](https://github.com/biomejs/biome/issues/4530)).

  Previously the rule removed the directives when a function expression was turned into an arrow function.
  The rule now correctly keeps the directives.

  ```diff
  - const withDirective = function () {
  + const withDirective = () => {
      "use server";
      return 0;
    }
  ```

- [#5044](https://github.com/biomejs/biome/pull/5044) [`bff5068`](https://github.com/biomejs/biome/commit/bff5068451507665b3bb2f9ea15bae9987d8aad6) Thanks [@ematipico](https://github.com/ematipico)! - [useSortedClasses](https://biomejs.dev/linter/rules/use-sorted-classes/) now suggests code fixes that match the JSX quote style of the formatter ([#4855](https://github.com/biomejs/biome/issues/4855)).
