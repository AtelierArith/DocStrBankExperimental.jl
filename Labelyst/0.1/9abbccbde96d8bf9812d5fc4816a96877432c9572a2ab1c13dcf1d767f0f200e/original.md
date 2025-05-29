```
labelyst(dataframe, output_file, paper_format::Vector{String}; <kwargs>)
labelyst(dataframe, output_file, paper_format::String, label_division::Vector{Int64}; <kwargs>)
labelyst(dataframe, output_file, paper_format::Vector{String}, label_division::Vector{Int64}; <kwargs>)
```

Take a `julia DataFrame` and produce a `.pdf` file with labels containing QR-codes and human readable codes.

### Keyword arguments

  * `font_size::String`: sets the font size for all the text on the label, default is `"12pt"`
  * `make_pdf::Bool`: define wether you want a `.pdf` as output or a raw `.typ` file, deault is `true`

# Examples

```julia
    # labels of size 90mm X 17mm, one per page, saved as "pot_labels.pdf"
    labelyst(dataframe, "pot_labels", ["90mm", "17mm"])

    # DIN A4 pages with 30 labels (10 rows x 3 cols), saved as "adh_labels.pdf"
    labelyst(dataframe, "adh_labels", "a4", [10, 3])

    # custom size pages with 50 labels per page (10 rows x 5 cols), saved as "cust_lab.pdf"
    labelyst(dataframe, "cust_lab", ["178mm", "250mm"], [10, 5]; font_size = "8pt") 
```
