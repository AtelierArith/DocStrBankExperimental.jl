```
H8sphere(radius::T, nrefine::IT) where {T<:Number, IT<:Integer}

半球の「radius」の1/8のメッシュを作成します。メッシュは「nrefine==0」の場合は4つの六面体要素で構成され、また「nrefine>0」の場合はそれ以上になります。「nrefine」はメッシュを細分化するために適用される二分の数です。
```
