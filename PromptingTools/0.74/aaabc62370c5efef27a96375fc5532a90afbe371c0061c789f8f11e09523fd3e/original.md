```
AICode(code::AbstractString; auto_eval::Bool=true, safe_eval::Bool=false, 
skip_unsafe::Bool=false, capture_stdout::Bool=true, verbose::Bool=false,
prefix::AbstractString="", suffix::AbstractString="", remove_tests::Bool=false, execution_timeout::Int = 60)

AICode(msg::AIMessage; auto_eval::Bool=true, safe_eval::Bool=false, 
skip_unsafe::Bool=false, skip_invalid::Bool=false, capture_stdout::Bool=true,
verbose::Bool=false, prefix::AbstractString="", suffix::AbstractString="", remove_tests::Bool=false, execution_timeout::Int = 60)
```

A mutable structure representing a code block (received from the AI model) with automatic parsing, execution, and output/error capturing capabilities.

Upon instantiation with a string, the `AICode` object automatically runs a code parser and executor (via `PromptingTools.eval!()`), capturing any standard output (`stdout`) or errors.  This structure is useful for programmatically handling and evaluating Julia code snippets.

See also: `PromptingTools.extract_code_blocks`, `PromptingTools.eval!`

# Workflow

  * Until `cb::AICode` has been evaluated, `cb.success` is set to `nothing` (and so are all other fields).
  * The text in `cb.code` is parsed (saved to `cb.expression`).
  * The parsed expression is evaluated.
  * Outputs of the evaluated expression are captured in `cb.output`.
  * Any `stdout` outputs (e.g., from `println`) are captured in `cb.stdout`.
  * If an error occurs during evaluation, it is saved in `cb.error`.
  * After successful evaluation without errors, `cb.success` is set to `true`.  Otherwise, it is set to `false` and you can inspect the `cb.error` to understand why.

# Properties

  * `code::AbstractString`: The raw string of the code to be parsed and executed.
  * `expression`: The parsed Julia expression (set after parsing `code`).
  * `stdout`: Captured standard output from the execution of the code.
  * `output`: The result of evaluating the code block.
  * `success::Union{Nothing, Bool}`: Indicates whether the code block executed successfully (`true`), unsuccessfully (`false`), or has yet to be evaluated (`nothing`).
  * `error::Union{Nothing, Exception}`: Any exception raised during the execution of the code block.

# Keyword Arguments

  * `auto_eval::Bool`: If set to `true`, the code block is automatically parsed and evaluated upon instantiation. Defaults to `true`.
  * `safe_eval::Bool`: If set to `true`, the code block checks for package operations (e.g., installing new packages) and missing imports, and then evaluates the code inside a bespoke scratch module. This is to ensure that the evaluation does not alter any user-defined variables or the global state. Defaults to `false`.
  * `skip_unsafe::Bool`: If set to `true`, we skip any lines in the code block that are deemed unsafe (eg, `Pkg` operations). Defaults to `false`.
  * `skip_invalid::Bool`: If set to `true`, we skip code blocks that do not even parse. Defaults to `false`.
  * `verbose::Bool`: If set to `true`, we print out any lines that are skipped due to being unsafe. Defaults to `false`.
  * `capture_stdout::Bool`: If set to `true`, we capture any stdout outputs (eg, test failures) in `cb.stdout`. Defaults to `true`.
  * `prefix::AbstractString`: A string to be prepended to the code block before parsing and evaluation. Useful to add some additional code definition or necessary imports. Defaults to an empty string.
  * `suffix::AbstractString`: A string to be appended to the code block before parsing and evaluation.  Useful to check that tests pass or that an example executes. Defaults to an empty string.
  * `remove_tests::Bool`: If set to `true`, we remove any `@test` or `@testset` macros from the code block before parsing and evaluation. Defaults to `false`.
  * `execution_timeout::Int`: The maximum time (in seconds) allowed for the code block to execute. Defaults to 60 seconds.

# Methods

  * `Base.isvalid(cb::AICode)`: Check if the code block has executed successfully. Returns `true` if `cb.success == true`.

# Examples

```julia
code = AICode("println("Hello, World!")") # Auto-parses and evaluates the code, capturing output and errors.
isvalid(code) # Output: true
code.stdout # Output: "Hello, World!
"
```

We try to evaluate "safely" by default (eg, inside a custom module, to avoid changing user variables).   You can avoid that with `save_eval=false`:

```julia
code = AICode("new_variable = 1"; safe_eval=false)
isvalid(code) # Output: true
new_variable # Output: 1
```

You can also call AICode directly on an AIMessage, which will extract the Julia code blocks, concatenate them and evaluate them:

```julia
msg = aigenerate("In Julia, how do you create a vector of 10 random numbers?")
code = AICode(msg)
# Output: AICode(Success: True, Parsed: True, Evaluated: True, Error Caught: N/A, StdOut: True, Code: 2 Lines)

# show the code
code.code |> println
# Output: 
# numbers = rand(10)
# numbers = rand(1:100, 10)

# or copy it to the clipboard
code.code |> clipboard

# or execute it in the current module (=Main)
eval(code.expression)
```
