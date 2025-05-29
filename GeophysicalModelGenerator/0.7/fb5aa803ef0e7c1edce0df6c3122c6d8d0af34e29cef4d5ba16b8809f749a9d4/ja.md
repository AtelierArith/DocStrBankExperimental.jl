```
inpoly(PolyX::Vector, PolyY::Vector, x::Number, y::Number, iSteps::Vector, jSteps::)
```

xとyで与えられた点が、PolyXとPolyYで与えられた多角形の内側または上にあるか（両方のケースでtrueを返す）をチェックします。iStepsとjStepsは多角形のエッジ間の接続性を提供します。この関数はinpolygon!()を通じて使用する必要があります。
