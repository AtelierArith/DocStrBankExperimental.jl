```
aref(x::GeometryStructure{S}, origin::Point{T}=zero(Point{S}); kwargs...) where
    {S <: Coordinate, T <: Coordinate}
```

`ArrayReference{float(T),typeof(x)}` オブジェクトを構築します。

キーワード引数は、列ベクトル、行ベクトル、列数、行数、x反射、拡大率、および回転を指定します。

これらのキーワードには同義語が受け入れられます：

  * 列ベクトル `dc::Point{T}`: `:deltacol`, `:dcol`, `:dc`, `:vcol`, `:colv`, `:colvec`, `:colvector`, `:columnv`, `:columnvec`, `:columnvector`
  * 行ベクトル: `:deltarow`, `:drow`, `:dr`, `:vrow`, `:rv`, `:rowvec`, `:rowvector`
  * 列数: `:nc`, `:numcols`, `:numcol`, `:ncols`, `:ncol`
  * 行数: `:nr`, `:numrows`, `:numrow`, `:nrows`, `:nrow`
  * X反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * 回転: `:rot`, `:rotation`, `:rotate`, `:angle`
