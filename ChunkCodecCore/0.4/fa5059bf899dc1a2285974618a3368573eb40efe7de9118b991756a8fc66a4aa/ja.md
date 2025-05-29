```
decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}) -> dst
```

デコーダー `d` を使用して、入力データ `src` を `dst` にデコードします。`d` は [`try_decode!`](@ref) を実装している必要があります。

デコードされた出力サイズが `length(dst)` と正確に一致しない場合は、[`DecodedSizeError`](@ref) をスローします。

入力データが無効であるためにデコードに失敗した場合は、[`DecodingError`](@ref) をスローします。

それ以外の場合は、エラーをスローします。

前提条件: `dst` と `src` はメモリ内で重複していないこと。

関連情報として [`decode`](@ref) と [`encode`](@ref) を参照してください。
