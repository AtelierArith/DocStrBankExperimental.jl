```
MarkdownVitepress(; repo, devbranch, devurl, kwargs...)
```

This is the main entry point for the Vitepress Markdown writer.  

It is a config which can be passed to the `format` keyword argument in `Documenter.makedocs`, and causes it to emit a Vitepress site.

!!! tip "Quick start"
    When invoking `Documenter.makedocs`, replace the default `format=Documenter.HTML(...)` with:

    ```julia
    format=DocumenterVitepress.MarkdownVitepress(; repo = "...", devbranch = "...", devurl = "...")
    ```


## Keyword arguments (config)

  * `repo`: *Required*: The full URL of the repository to which the documentation will be deployed.
  * `devbranch`: The name of the development branch, like `master` or `main`.
  * `devurl`: The URL path to the development site, like `dev` or `dev-branch`.
  * `deploy_url`: The URL of the repository to which the documentation will be deployed. This **must** be the full URL, **including `https://`**, like `https://rafaqz.github.io/Rasters.jl` or `https://geo.makie.jl/`.

  * `description`: A description of the website as a String.
  * `build_vitepress`: Determines whether to build the Vitepress site or only emit markdown files.  Defaults to `true`, i.e., building the full Vitepress site.
  * `install_npm`: Determines whether to run `npm install` before building the Vitepress site.  Defaults to `true`.
  * `md_output_path`: The path to which the Markdown files will be output.  Defaults to `$build/.documenter`.
  * `deploy_decision`: DeployDecision from Documenter.jl. This is used to determine whether to deploy the documentation or not. Options are:

      * `nothing`: **Default**. Automatically determine whether to deploy the documentation.
      * `Documenter.DeployDecision`: Override the automatic decision and deploy based on the passed config.

    It might be useful to use the latter if DocumenterVitepress fails to deploy automatically. You can pass a manually constructed `Documenter.DeployDecision` struct, or the output of `Documenter.deploy_folder(Documenter.auto_detect_deploy_system(); repo, devbranch, devurl, push_preview)`.

  * `assets`: A list of assets, the same as what is provided to Documenter's HTMLWriter.
  * `inventory_version`: A version string to write to the header of the objects.inv inventory file. This should be a valid version number without a v prefix. Defaults to the version defined in the Project.toml file in the parent folder of the documentation root
  * `keep`: Sets the granularity of versions which should be kept. Options are :patch, :minor or :breaking (the default). You can use this to reduce the number of docs versions that coexist on your dev branch. With :patch, every patch version will be stored. With :minor, v1.1.0, v1.1.1, v1.1.2 etc. will overwrite each other as v1.1. With :breaking, only the major versions v1, v2, v3 etc. will be kept, except below v1 where each minor version will be kept, as these are considered breaking under Julia's interpretation of SemVer.

## Extended help

The `repo` kwarg is used to set the edit link for the documentation.

The `devbranch` and `devurl` kwargs are used to set the path of the static site, which Vitepress expects in advance.
