```
function register!(mapper::DBMapper, d::Type{T}; table_name::String="") where T <: Model
```

タイプ T の要素をマッパーに登録します。指定されたモデルのためにテーブルタイプが作成され、データベースに保存されます。この関数は、このライブラリで使用したい各タイプに対して呼び出す必要があります。
