```
set_titles!(axs::Array;
            labels::Array{String,1} = String[],
            paren::Bool = true,
            capital::Bool = false,
            dotsep::Bool = false,
            fontsize::Number = 16,
            loc::String = "center",
            usetex::Bool = true
)
```

Set titles for the axes, given

  * `axs` An array of axis
  * `labels` Optional: labels after the panel title, e.g., `(a) label`
  * `paren` Optional: if true, use format like `(a)`
  * `capital` Optional: if true, use capital letters like `(A)`
  * `dotsep` Optional: if true, add a dot after the label like `(a).`
  * `fontsize` Optional: fontsize of the title
  * `loc` Optional: location of the title
  * `usetex` Optional: use latex render
