```
make_tiers(dem_settings::Vector{T}) where  {T <: Tuple{Real, Real}}
```

タプルのベクターをDemTiersに変換します。最初の区間は常に0から始まり、最後の区間は常に上限が無制限です。ティアは低いものから高いものへとソートされます。
