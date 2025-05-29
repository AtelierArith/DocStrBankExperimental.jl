```
BuildOptions(
    dir::AbstractString;
    write_files::Bool=true,
    previous_dir::Union{Nothing,AbstractString}=nothing,
    output_format::Union{OutputFormat,Vector{OutputFormat}}=html_output,
    add_documenter_css::Bool=true,
    use_distributed::Bool=true,
    compiler_options::Union{Nothing,CompilerOptions}=nothing,
    max_concurrent_runs::Int=4
)
```

Arguments:

  * `dir`:   Directory in which the Pluto notebooks are stored.
  * `write_files`:   Write files to `joinpath(dir, "$file.html")`.
  * `previous_dir::Union{Nothing,AbstractString}=Nothing`:   Use the output from the previous run as a cache to speed up running time.   To use the cache, specify a directory `previous_dir::AbstractString` which contains HTML or Markdown files from a previous run.   Specifically, files are expected to be at `joinpath(previous_dir, "$file.html")`.   The output from the previous run may be embedded in a larger HTML or Markdown file.   This package will extract the original output from the full file contents.   By default, caching is disabled.
  * `output_format`:   What file to write the output to.   By default this is `html_output::OutputFormat` meaning that the output of the HTML method is pure HTML.   To generate Franklin, Documenter or PDF files, use respectively `franklin_output`, `documenter_output` or `pdf_output`.   When `BuildOptions.write_files == true` and `output_format == franklin_output` or `output_format == documenter_output`, the output file has a ".md" extension instead of ".html".   When `BuildOptions.write_files == true` and `output_format == pdf_output`, two output files are created with ".tex" and ".pdf" extensions.
  * `add_documenter_css` whether to add a CSS style to the HTML when `documenter_output=true`.
  * `use_distributed`:   Whether to build the notebooks in different processes.   By default, this is enabled just like in Pluto and the notebooks are build in parallel.   The benefit of different processes is that things are more independent of each other.   Unfortunately, the drawback is that compilation has to happen for each process.   By setting this option to `false`, all notebooks are built sequentially in the same process which avoids recompilation.   This is likely quicker in situations where there are few threads available such as GitHub Runners depending on the notebook contents.   Beware that `use_distributed=false` will **not** work with Pluto's built-in package manager.
  * `compiler_options`:   `Pluto.Configuration.CompilerOptions` to be passed to Pluto.   This can, for example, be useful to pass custom system images from `PackageCompiler.jl`.
  * `max_concurrent_runs`:   Maximum number of notebooks to evaluate concurrently when `use_distributed=true`.   Note that each notebook starts in a different process and can start multiple threads, so don't set this number too high or the CPU might be busy switching tasks and not do any productive work.
