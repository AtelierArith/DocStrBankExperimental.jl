```
preview_demos(demo_path; kwargs...)
```

Generate a docs preview for a single demo card.

# Return values

  * `index_file`: absolute path to the index file of the demo page. You can open this in your browser and see the generated demos.

# Arguments

  * `demo_path`: path to your demo file or folder. It can be path to the demo file, the folder of multiple scripts. If standard demo page folder structure is detected, use it, and otherwise will create a preview version of it.

# Parameters

  * `theme`: the card theme you want to use in the preview. By default, it infers from your page config file. To not generate index page, you could pass `nothing` to it. See also [`cardtheme`](@ref DemoCards.cardtheme) for theme choices.
  * `assets = String[]`: this is passed to `Documenter.HTML`
  * `edit_branch = "master"`: same to that in `makedemos`
  * `credit = true`: same to that in `makedemos`
  * `throw_error = false`: same to that in `makedemos`
  * `require_html = true`: if it needs to trigger the Documenter workflow and generate HTML preview. If set to `false`, the return value is then the path to the generated `index.md` file. This is an experimental keyword and should not be considered stable.
  * `clean = true`: whether you need to first clean up the existing sandbox building dir.
