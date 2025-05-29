データを生成または消費するメソッドのスーパタイプ。

```
                 ╭────loader─────╮
                 ╵               ▼
Storage ◀────▶ Data          Information
                 ▲               ╷
                 ╰────writer─────╯
```

サブタイプは3つあります：

  * `DataStorage`
  * `DataLoader`
  * `DataWrite`

各サブタイプは、データ操作を実行するために使用されるドライバーを指定する `Symbol` 型パラメータを取ります。さらに、各サブタイプには以下のフィールドがあります：

  * `dataset::DataSet`、メソッドが操作するデータセット
  * `type::Vector{<:QualifiedType}`、メソッドがサポートするJulia型
  * `priority::Int`、このメソッドが他の選択肢と比較して使用される優先度。値が低いほど優先度が高くなります。
  * `parameters::SmallDict{String, Any}`、メソッドに適用される任意のパラメータ。
