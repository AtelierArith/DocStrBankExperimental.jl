```
nbexport(io, nbpath; regex=r"", markdown=true)
nbexport(output_filename, nbpath; regex=r"", markdown=true)
```

Read the IJulia Jupyter notebook file `nbpath` and output it as ordinary Julia code to the `io` stream or to the `output_filename` file.

Markdown cells in the notebook are parsed and converted to `# ...` comments, unless the `markdown` keyword argument is set to `false` (in which case Markdown cells are ignored).

Similar to `@nbinclude`, code cells not matching the regular expression passed via the `regex` keyword are ignored.
