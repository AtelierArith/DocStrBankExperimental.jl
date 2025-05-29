```
@quickcheck qc [file_id::AbstractString="yyyy-mm-dd_HH-MM-SS"]
```

オブジェクト `qc` のプロパティを確認します。型は [`Quickcheck`](@ref) です。

もし `qc.serialize_fails` が `true` の場合、失敗したケースを `JCheck_<file_id>.jchk` にシリアライズします。それらは後で [`load`](@ref) と [`@getcases`](@ref) を使用して分析できます。

# 注意

引数 `file_id` が渡されない場合、現在の時間がデフォルトとなります。
