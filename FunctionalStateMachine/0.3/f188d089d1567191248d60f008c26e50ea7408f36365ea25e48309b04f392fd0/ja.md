状態遷移機能を実行する（ファンクタとして）。

ノート

  * `timeout::Union{Real,Nothing}` はオプションでデフォルト `=nothing`。

      * このコードは、使用されない場合、低下したコードおよびllvmコードではスキップされます。
      * サブルーチンは、`timeout::Real` [秒] の期間中に調査するために `pollinterval::Real` [秒] を使用します。
  * 次のいずれかを使用してFSMを早期に停止できます：

      * `breakafter`、`iterlimit`。
  * デバッグを助けるために、関数 `st.next` の前に `injectDelayBefore` を挿入できます。
  * `verbose=true` を使用してFSMのステップを印刷できます。

      * `verbosefid::IOStream` は冗長出力の宛先として使用され、デフォルトは `stdout` です。
  * FSMのステップと `userdata` は、`recordhistory=true` を使用して標準の `history` 形式で記録できます。
  * `housekeeping_cb` は、ユーザーに `StateMachine` の内部へのアクセスを提供し、特注の操作を挿入する機会を与えるコールバックです。

例

```julia
bar!(usrdata) = IncrementalInference.exitStateMachine
foo!(usrdata) = bar!

sm = StateMachine(next=foo!)
usrdata = nothing
while st(usrdata); end
```
