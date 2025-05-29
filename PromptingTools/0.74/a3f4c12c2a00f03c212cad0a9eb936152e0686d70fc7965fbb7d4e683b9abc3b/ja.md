```
recursive_splitter(text::String; separator::String=" ", max_length::Int=35000) -> Vector{String}
```

指定された最大長 `max_length` のチャンクに、与えられた文字列 `text` を分割します。これは、より大きな文書やテキストを、より小さなセグメントに分割するのに特に便利で、モデルやシステムの小さなコンテキストウィンドウに適しています。

複数のセパレーターに対してディスパッチするメソッド `recursive_splitter(text::String, separators::Vector{String}; max_length::Int=35000) -> Vector{String}` があり、Langchain の `RecursiveCharacterTextSplitter` のロジックを模倣しています。

# 引数

  * `text::String`: 分割されるテキスト。
  * `separator::String=" "`: テキストをミニチャンクに分割するために使用されるセパレーター。デフォルトはスペース文字です。
  * `max_length::Int=35000`: 各チャンクの最大長。デフォルトは35,000文字で、16Kのコンテキストウィンドウに収まるはずです。

# 戻り値

`Vector{String}`: 元のテキストのチャンクを表す文字列のベクターで、`max_length` 以下の大きさです。

# 注意事項

  * 関数は、各チャンクが `max_length` にできるだけ近くなるようにし、超えないようにします。
  * `text` が空の場合、関数は空の配列を返します。
  * 分割後、セパレーターはテキストチャンクに再追加され、元のテキストの構造をできるだけ保持します。

# 例

デフォルトのセパレーター（" "）でテキストを分割する：

```julia
text = "Hello world. How are you?"
chunks = recursive_splitter(text; max_length=13)
length(chunks) # 出力: 2
```

カスタムセパレーターとカスタム `max_length` を使用する：

```julia
text = "Hello,World," ^ 2900 # 長さ 34900 文字
recursive_splitter(text; separator=",", max_length=10000) # 4K コンテキストウィンドウ用
length(chunks[1]) # 出力: 4
```
