```
dcc_markdown(;kwargs...)
dcc_markdown(children::Any, kwargs...)
dcc_markdown(children_maker::Function, kwargs...)
```

A Markdown component A component that renders Markdown text as specified by the GitHub Markdown spec. These component uses [react-markdown](https://rexxars.github.io/react-markdown/) under the hood.

  * `children` (String | Array of Strings; optional): A markdown string (or array of strings) that adheres to the CommonMark spec
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): Class name of the container element
  * `dangerously_allow_html` (Bool; optional): A boolean to control raw HTML escaping.

Setting HTML from code is risky because it's easy to inadvertently expose your users to a cross-site scripting (XSS) (https://en.wikipedia.org/wiki/Cross-site_scripting) attack.

  * `dedent` (Bool; optional): Remove matching leading whitespace from all lines.

Lines that are empty, or contain *only* whitespace, are ignored. Both spaces and tab characters are removed, but only if they match; we will not convert tabs to spaces or vice versa.

  * `highlight_config` (lists containing elements theme   - `theme` ('dark', 'light'; optional): Color scheme; default 'light'; optional): Config options for syntax highlighting.
  * `link_target` (String; optional): A string for the target attribute to use on links (such as "_blank")
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `mathjax` (Bool; optional): If true, loads mathjax v3 (tex-svg) into the page and use it in the markdown
  * `style` (Dict; optional): User-defined inline styles for the rendered Markdown
