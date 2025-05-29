```julia
serve(
;
    clear,
    verb,
    port,
    single,
    prerender,
    nomess,
    isoptim,
    no_fail_prerender,
    eval_all,
    silent,
    cleanup
)

```

Runs JuDoc in the current directory.

Keyword arguments:

  * `clear=false`:     whether to remove any existing output directory
  * `verb=false`:      whether to display messages
  * `port=8000`:       the port to use for the local server (should pick a number between 8000 and 9000)
  * `single=false`:    whether to run a single pass or run continuously
  * `prerender=false`: whether to pre-render javascript (KaTeX and highlight.js)
  * `nomess=false`:    suppresses all messages (internal use).
  * `isoptim=false`:   whether we're in an optimisation phase or not (if so, links are fixed in case                    of a project website, see [`write_page`](@ref).
  * `no_fail_prerender=true`: whether, in a prerendering phase, ignore errors and try to produce an output
  * `eval_all=false`:  whether to force re-evaluation of all code blocks
  * `silent=false`:    switch this on to suppress all output (including eval statements).
  * `cleanup=true`:    whether to clear environment dictionatires, see [`cleanup`](@ref).
