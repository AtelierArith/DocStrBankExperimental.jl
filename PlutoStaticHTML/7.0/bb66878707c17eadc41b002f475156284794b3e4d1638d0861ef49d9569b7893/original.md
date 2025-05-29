```
OutputOptions(;
    code_class::AbstractString="language-julia",
    output_pre_class::AbstractString="code-output documenter-example-output",
    hide_code::Bool=false,
    hide_md_code::Bool=true,
    hide_md_def_code::Bool=true,
    add_state::Bool=true,
    append_build_context::Bool=false,
    show_output_above_code::Bool=false,
    replace_code_tabs::Bool=true,
    convert_admonitions::Bool=true
)
```

Arguments:

  * `code_class`:   HTML class for code.   This is used by CSS and/or the syntax highlighter.
  * `output_pre_class`:   HTML class for `<pre>`.
  * `output_class`:   HTML class for output.   This is used by CSS and/or the syntax highlighter.
  * `hide_code`:   Whether to omit all code blocks.   Can be useful when readers are not interested in code at all.
  * `hide_md_code`:   Whether to omit all Markdown code blocks.
  * `hide_md_def_code`:   Whether to omit Franklin Markdown definition code blocks (blocks surrounded by +++).
  * `add_state`:   Whether to add a comment in HTML with the state of the input notebook.   This state can be used for caching.   Specifically, this state stores a checksum of the input notebook and the Julia version.
  * `append_build_context`:   Whether to append build context.   When set to `true`, this adds information about the dependencies and Julia version.   This is not executed via Pluto.jl's evaluation to avoid having to add extra dependencies to existing notebooks.   Instead, this reads the manifest from the notebook file.
  * `show_output_above_code`:   Whether to show the output from the code above the code.   Pluto.jl shows the output above the code by default; this package shows the output below the code by default.   To show the output above the code, set `show_output_above_code=true`.
  * `replace_code_tabs`:   Replace tabs at the start of lines inside code blocks with spaces.   This avoids inconsistent appearance of code blocks on web pages.
  * `convert_admonitions`:   Convert admonitions such as   `!!! note       This is a note.`   from Pluto's HTML to Documenter's HTML.   When this is enabled, the `documenter_output` has proper styling by default.
