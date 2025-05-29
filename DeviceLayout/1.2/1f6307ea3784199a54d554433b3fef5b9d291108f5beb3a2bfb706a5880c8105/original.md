```
ArrayReference(x::GeometryStructure{S}; kwargs...) where {S <: Coordinate}
ArrayReference(x::GeometryStructure{S}, origin::Point{T}; kwargs...) where
    {S <: Coordinate, T <: Coordinate}
ArrayReference(x, origin::Point{T}; kwargs...) where {T <: Coordinate}
```

Construct a `ArrayReference{float(T),typeof(x)}` object.

Keyword arguments specify the column vector, row vector, number of columns, number of rows, x-reflection, magnification factor, and rotation.

Synonyms are accepted for these keywords:

  * Column vector `dc::Point{T}`: `:deltacol`, `:dcol`, `:dc`, `:vcol`, `:colv`, `:colvec`, `:colvector`, `:columnv`, `:columnvec`, `:columnvector`
  * Row vector: `:deltarow`, `:drow`, `:dr`, `:vrow`, `:rv`, `:rowvec`, `:rowvector`
  * Number of columns: `:nc`, `:numcols`, `:numcol`, `:ncols`, `:ncol`, `:col`
  * Number of rows: `:nr`, `:numrows`, `:numrow`, `:nrows`, `:nrow`, `:col`
  * X-reflection: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * Magnification: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * Rotation: `:rot`, `:rotation`, `:rotate`, `:angle`
