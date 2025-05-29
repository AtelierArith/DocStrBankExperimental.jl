```
GenerativeBeliefMDP(pomdp, updater)
GenerativeBeliefMDP(pomdp, updater; terminal_behavior=TerminalStateTerminalBehavior())
```

POMDP `pomdp` に対応する信念 MDP の生成モデルを作成し、`updater` によって信念の更新を行います。各ステップは、現在の信念から状態をサンプリングし、その状態とアクションから観測を生成し、次に `updater` を使用して信念を更新することによって実行されます。

信念は、サポート内のすべての POMDP 状態が非ゼロ確率で端末である場合に端末と見なされます。

信念から端末の POMDP 状態がサンプリングされたときのデフォルトの動作は、[`terminalstate`](@ref) に遷移することです。これは、`terminal_behavior` キーワード引数によって制御できます。`terminal_behavior=ContinueTerminalBehavior(pomdp, updater)` を使用すると、サンプリングされた状態が端末であっても MDP が信念の更新を試み続けるようになります。`terminal_behavior` に `Function` または引数 `b, s, a, rng` を受け取り新しい信念を返す呼び出し可能オブジェクトを提供することで、さらにカスタマイズできます（例として `ContinueTerminalBehavior` の実装を参照してください）。`determine_gbmdp_state_type` を使用して、動作をさらにカスタマイズすることもできます。
