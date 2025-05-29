```julia
optimize(
;
    prerender,
    minify,
    sig,
    prepath,
    no_fail_prerender,
    suppress_errors,
    cleanup
)

```

Does a full pass followed by a pre-rendering and minification step.

  * `prerender=true`: whether to pre-render katex and highlight.js (requires `node.js`)
  * `minify=true`:    whether to minify output (requires `python3` and `css_html_js_minify`)
  * `sig=false`:      whether to return an integer indicating success (see [`publish`](@ref))
  * `prepath=""`:     set this to something like "project-name" if it's a project page
  * `no_fail_prerender=true`:  whether to ignore errors during the pre-rendering process
  * `suppress_errors=true`:    whether to suppress errors
  * `cleanup=true`:   whether to empty environment dictionaries

Note: if the prerendering is set to `true`, the minification will take longer as the HTML files will be larger (especially if you have lots of maths on pages).
