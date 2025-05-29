```julia
optimize(
;
    prepath,
    version,
    prerender,
    minify,
    sig,
    no_fail_prerender,
    on_write,
    suppress_errors,
    clear,
    cleanup,
    fail_on_warning
)

```

Does a full pass followed by a pre-rendering and minification step.

  * `prepath=""`:     set this to something like "project-name" if it's a project                    page (usually this is set via config.md)
  * `version=""`:     if "dev", the base url will be `/{prepath}/dev/`, if "xxx",                    the base url will be `/{prepath}/stable/`, a copy of                    the website will also be at `/{prepath}/xxx/` an example                    would be `version="v0.15.2"`. If left empty, the base url                    is just `/{prepath}/`.
  * `is_preview=false`: if true, then no matter what the version given is, it will                      not update `/stable/` and `/dev/`.
  * `prerender=true`: whether to pre-render katex and highlight.js (requires                    `node.js`)
  * `minify=true`:    whether to minify output (requires `python3` and                    `css_html_js_minify`)
  * `sig=false`:      whether to return an integer indicating success (see                    [`publish`](@ref))
  * `clear=false`:    whether to clear the output dir and thereby regenerate                    everything
  * `no_fail_prerender=true`: whether to ignore errors during the pre-rendering                            process
  * `suppress_errors=true`:   whether to suppress errors
  * `fail_on_warning=false`:   if true, warnings become fatal errors
  * `cleanup=true`:   whether to empty environment dictionaries
  * `on_write(pg, fd_vars)`: callback function after the page is rendered,                     passing as arguments the rendered page and the page                     variables

Note: if the prerendering is set to `true`, the minification will take longer as the HTML files will be larger (especially if you have lots of maths on pages).
