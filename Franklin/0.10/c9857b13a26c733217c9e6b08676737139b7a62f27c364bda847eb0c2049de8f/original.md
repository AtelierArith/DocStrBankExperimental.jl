```julia
serve(
;
    clear,
    verb,
    port,
    single,
    prerender,
    nomess,
    is_final_pass,
    no_fail_prerender,
    eval_all,
    silent,
    cleanup,
    on_write,
    log,
    host,
    show_warnings,
    fail_on_warning,
    launch,
    no_set_paths,
    join_to_prepath
)

```

Runs Franklin in the current directory.

Keyword arguments:

  * `clear=false`:            whether to remove any existing output directory
  * `verb=false`:             whether to display messages
  * `port=8000`:              the port to use for the local server (should pick a number                           between 8000 and 9000)
  * `single=false`:           whether to run a single pass or run continuously
  * `nomess=false`:           suppresses all messages (internal use).
  * `is_final_pass=false`:    whether we're in a "final pass" (if so, links are                           fixed in case of a project website, see                           [`convert_and_write`](@ref).
  * `prerender=false`:        whether to pre-render javascript (KaTeX and highlight.js)
  * `no_fail_prerender=true`: whether, in a prerendering phase, ignore errors and                           try to produce an output
  * `eval_all=false`:         whether to force re-evaluation of all code blocks
  * `silent=false`:           switch this on to suppress all output (including eval                           statements).
  * `cleanup=true`:           whether to clear environment dictionaries, see                           [`cleanup`](@ref).
  * `on_write(pg, fd_vars)`:  callback function after the page is rendered,                           passing as arguments the rendered page and the page                           variables
  * `host="127.0.0.1"`:       the host to use for the local server
  * `show_warnings=true`:     whether to show franklin  warnings
  * `launch=!single`:         whether to launch the browser when serving
