```
T10block(
    Length::T,
    Width::T,
    Height::T,
    nL::IT,
    nW::IT,
    nH::IT;
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

長方形ブロックのT10要素の四面体メッシュを生成します。
