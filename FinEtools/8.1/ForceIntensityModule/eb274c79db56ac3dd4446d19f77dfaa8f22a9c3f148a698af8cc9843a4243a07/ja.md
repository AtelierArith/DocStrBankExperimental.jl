```
updateforce!(self::ForceIntensity, XYZ::Matrix{T}, tangents::Matrix{T}, feid::IT, qpid::IT) where {T<:Number, IT<:Integer}
```

力の強度ベクトルを更新します。

ベクトルを返します（キャッシュ `self.cache` に保存されます）。
