```
HtmlTableFormat
```

Format that will be used to print the HTML table. All parameters are strings compatible with the corresponding HTML property.

# Fields

  * `css::String`: CSS to be injected at the end of the `<style>` section.
  * `table_width::String`: Table width.

# Remarks

Besides the usual HTML tags related to the tables (`table`, `td,`th`,`tr`, etc.), there are three important classes that can be used to format tables using the variable`css`.

  * `header`: This is the class of the header (first line).
  * `subheader`: This is the class of the sub-headers (all the rest of the lines in the header   section).
  * `headerLastRow`: The last row of the header section has additionally this class.
  * `rowNumber`: All the cells related to the row number have this class. Thus, the row number   header can be styled using `th.rowNumber` and the row numbers cells can be styled using   `td.rowNumber`.
