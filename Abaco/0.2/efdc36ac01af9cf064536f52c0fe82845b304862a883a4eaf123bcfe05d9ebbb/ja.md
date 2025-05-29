```
abaco_init(onresult; handle=nothing, interval::Int=900, ages::Int=4, emitone=true)::Context
```

abacoコンテキストを初期化します：

  * `onresult`: 数式の値が計算されるたびに呼び出される関数コールバック。
  * `handle`: ユーザー定義のオブジェクト。            handleが定義されている場合、それは`onresult`の最初の引数となり、デフォルトは`nothing`。
  * `interval`: 秒単位のスパン間隔、デフォルトは900秒（15分）。             intervalが-1に等しい場合、無限の時間スパンが1つだけ存在します。
  * `ages`: abacoによって管理されるアクティブなropsの数。デフォルトは4。         `interval`が-1に等しい場合、`ages`は意味を失うため適用されません。
  * `emitone`: `true`の場合、各時間スパンごとに最大1つの数式値を発信し、             そうでない場合は新しい入力ごとに新しい結果を発信します。デフォルトは`true`です。

例1: handleオブジェクトを使用する`onresult`コールバックの定義。

```
# handleオブジェクトはソケットです
sock = connect(3001)

function onresult(handle, ts, ne, formula_name, value, inputs)
    # ts, ne, ...からpktメッセージを構築します
    pkt = ...
    write(sock, pkt)
end
```

例2: handleオブジェクトを使用しない`onresult`コールバックの定義。

```julia
abaco = abaco_init(onresult, handle=sock)

function onresult(ts, ne, formula_name, value, inputs)
    @info "[$ts][$ne] 関数 $fname=$value"
end

abaco = abaco_init(onresult)
```
