```
is_probable_supersingular(E::EllipticCurve{T}) where T <: FinFieldElem
```

確率的アルゴリズムを使用して、Eが超特異であるかどうかをテストします。関数がfalseを返す場合、曲線は普通であることが証明されます。関数がtrueを返す場合、曲線が超特異である可能性が高いですが、結果は証明されていません。
