作成チャット

# 引数:

  * `api_key::String`: OpenAI APIキー
  * `model_id::String`: モデルID
  * `messages::Vector`: これまでのチャット履歴。
  * `streamcallback=nothing`: ストリーミングモードでチャット応答の各チャンク（デルタ）に対して呼び出す関数。

# キーワード引数（詳細なリストについてはOpenAIのドキュメントを確認してください）:

  * `temperature::Float64=1.0`: 0から2の間で使用するサンプリング温度。0.8のような高い値は出力をよりランダムにし、0.2のような低い値はより焦点を絞り、決定論的にします。一般的には、これまたはtop_pを変更することをお勧めしますが、両方は変更しないでください。
  * `top_p::Float64=1.0`: 温度を使ったサンプリングの代替手段で、核サンプリングと呼ばれ、モデルはtop_p確率質量を持つトークンの結果を考慮します。したがって、0.1は上位10%の確率質量を構成するトークンのみが考慮されることを意味します。一般的には、これまたはtemperatureを変更することをお勧めしますが、両方は変更しないでください。

!!! 注     ここで`stream=true`オプションを使用しないでください。代わりに`streamcallback`キーワード引数を使用してください（以下の関連セクションを参照）。

エンドポイントおよび追加引数の詳細については、[https://platform.openai.com/docs/api-reference/chat](https://platform.openai.com/docs/api-reference/chat)を訪問してください。

# HTTP.requestキーワード引数:

  * `http_kwargs::NamedTuple=NamedTuple()`: HTTP.requestに渡すキーワード引数（例：`http_kwargs=(connection_timeout=2,)`で接続タイムアウトを2秒に設定）。

## 例:

```julia
julia> CC = create_chat("..........", "gpt-4o-mini", 
    [Dict("role" => "user", "content"=> "OpenAIのミッションは何ですか？")]
);

julia> CC.response.choices[1][:message][:content]
"

OpenAIのミッションは、安全で人類に利益をもたらす人工知能（AI）を創造し、人類がその潜在能力を最大限に発揮できるようにすることです。この組織は、安全で人間の価値観に沿ったAIの技術的アプローチを発見し、開発することを目指しています。OpenAIは、AIが気候変動、疾病、不平等、貧困など、世界の最も差し迫った問題のいくつかを解決するのに役立つと信じています。この組織は、AIの研究と開発を進めることにコミットし、倫理的かつ責任を持って使用されることを確保しています。"
```

### ストリーミング

単一の`String`を引数として受け取る関数が`streamcallback`引数に渡されると、ストリーミングモードでリクエストが行われます。`streamcallback`コールバックは、ストリーミング応答の各行に対して呼び出されます。ここでは、異なる部分の応答が異なる時間に受信される様子を示すために、現在の時間を出力するコールバックを使用します。

応答ボディは応答のチャンク化された性質を反映するため、APIから返された完全なメッセージを回復するためにいくつかの再構成が必要になります。

```julia
julia> CC = create_chat(key, "gpt-4o-mini",
           [Dict("role" => "user", "content"=> "ニューヨークはどの大陸にありますか？二語の答え。")],
       streamcallback = x->println(Dates.now()));
       2023-03-27T12:34:50.428
2023-03-27T12:34:50.524
2023-03-27T12:34:50.524
2023-03-27T12:34:50.524
2023-03-27T12:34:50.545
2023-03-27T12:34:50.556
2023-03-27T12:34:50.556

julia> map(r->r["choices"][1]["delta"], CC.response)
5-element Vector{JSON3.Object{Base.CodeUnits{UInt8, SubString{String}}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}:
 {
   "role": "assistant"
}
 {
   "content": "北"
}
 {
   "content": "アメリカ"
}
 {
   "content": "。"
}
 {}
```
