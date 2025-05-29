```
addarr!(
    c1::AbstractCoordinateSystem{T},
    c2::GeometryStructure,
    origin::Point=zero(Point{T});
    kwargs...
)
```

Add an `ArrayReference` to `c2` to the list of references in `c1`.

The reference to `c2` has origin `origin`. Keyword arguments specify the column vector, row vector, number of columns, number of rows, x-reflection, magnification factor, and rotation.

Synonyms are accepted for these keywords:

  * Column vector `dc::Point{T}`: `:deltacol`, `:dcol`, `:dc`, `:vcol`, `:colv`, `:colvec`, `:colvector`, `:columnv`, `:columnvec`, `:columnvector`
  * Row vector: `:deltarow`, `:drow`, `:dr`, `:vrow`, `:rv`, `:rowvec`, `:rowvector`
  * Number of columns: `:nc`, `:numcols`, `:numcol`, `:ncols`, `:ncol`
  * Number of rows: `:nr`, `:numrows`, `:numrow`, `:nrows`, `:nrow`
  * X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
