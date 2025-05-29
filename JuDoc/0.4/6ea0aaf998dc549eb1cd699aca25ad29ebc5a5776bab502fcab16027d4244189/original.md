```julia
publish(
;
    prerender,
    minify,
    nopass,
    prepath,
    message,
    cleanup,
    final
)

```

This is a simple wrapper doing a git commit and git push without much fanciness. It assumes the current directory is a git folder. It also fixes all links if you specify `prepath` (or if it's set in `config.md`).

**Keyword arguments**

  * `prerender=true`:      prerender javascript before pushing see [`optimize`](@ref)
  * `minify=true`:         minify output before pushing see [`optimize`](@ref)
  * `nopass=false`:        set this to true if you have already run `optimize` manually.
  * `prepath=""`:          set this to something like "project-name" if it's a project page
  * `message="jd-update"`: add commit message.
  * `cleanup=true`:        whether to cleanup environment dictionaries (should stay true).
  * `final=nothing`:       a function `()->nothing` to execute last, before doing the git push.                        It can be used to refresh a Lunr index, generate notebook files with                        Literate, etc, ... You might want to compose `jdf_*` functions that are                        exported by JuDoc (or imitate those). It can access GLOBAL*PAGE*VARS.
