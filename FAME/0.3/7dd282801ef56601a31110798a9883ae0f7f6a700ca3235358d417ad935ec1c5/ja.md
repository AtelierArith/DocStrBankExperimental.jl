```
listdb(db::FameDatabase, [wc; filters...])
```

データベース内のオブジェクトを、指定されたワイルドカードとフィルターに基づいてリストします。[`Vector{FameObject}`](@ref FameObject)を返します。

ワイルドカード`wc`は、ワイルドカード文字を含む文字列です。'^'は任意の1文字に一致し、'?'は任意の0文字以上に一致します。指定しない場合、デフォルトは'?'で、データベース全体をリストします。

フィルター:

  * `alias::Bool` - エイリアス名に一致するかどうか。
  * `class::String` - 一致させるオブジェクトのクラス。複数のクラスをカンマ区切りの文字列で指定できます。例: `class="SERIES,SCALAR"`。
  * `type::String` - 一致させるオブジェクトのタイプ。例: `type="NUMERIC,PRECISION"`。
  * `freq::String` - 一致させるオブジェクトの頻度。例: `freq="QUARTERLY"`。
