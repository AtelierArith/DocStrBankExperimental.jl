```
substitute_latex(md::AbstractString, scale::Number, im_dir; extra_packages="")::String
```

Substitute LaTeX in Markdown string `md`. The LaTeX images will be placed at `im_dir/<h>.svg` where `h` is a hash calculated over the math expression. Tweaking the image size is possible by setting `scale`.

The benefit of using a hash is that the browser downloads only one image per math expression.
