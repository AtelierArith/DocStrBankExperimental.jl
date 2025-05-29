```
issingular(bsamp::MixedModelFitCollection;
           atol::Real=0, rtol::Real=atol>0 ? 0 : √eps))
```

各ブートストラップサンプルの対応するフィットの特異性をテストします。

小さな非負のθ値は`fit!`で0に置き換えられるため、等号比較が使用されます。

[`issingular(::MixedModel)`](@ref)も参照してください。
