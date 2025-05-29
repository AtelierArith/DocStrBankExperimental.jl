```
plan_ntt(len::Integer, p::Integer, npru::Integer; memoryefficient = false) -> Tuple{NTTPlan, INTTPlan}
```

NTTPlanと逆のINTTPlanを返します。これらは`ntt!()`と`intt!()`で使用されます。NTTのタイプはpによって決定され、`Union{Int32, Int64, UInt32, UInt64}`のいずれかでなければなりません。

# 引数:

  * `len`: NTTの長さ（2の累乗でなければなりません）
  * `p`: NTTを実行するフィールドの特性。
  * `npru`: `p`のlen-th原始根。検証は行われません。生成には`primitive_nth_root_of_unity()`を参照してください。
  * `memoryefficient`: 原始根テーブルを生成するかどうかを決定するブール値。falseの場合、NTTは遅くなりますが、メモリは半分になります。
