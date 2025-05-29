```
RecordAction
```

`RecordAction`は値を記録するための小さなファンクタです。通常の呼び出しは次のようになります。

```
(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, k) -> s
```

これは現在の問題とソルバーの組み合わせに対して記録を行い、`k`は現在の反復を示します。

慣例として`i=0`は「初期化のみ」と解釈されるため、内部値のみを初期化し、記録をトリガーしません。これは[`stop_solver!`](@ref)から呼び出され、その後trueを返します。

負の値は「リセット」として解釈され、したがってすべての保存された記録を削除する必要があります。たとえば、`RecordAction`を再利用する場合です。ソルバーの開始時には、`-1`を使って`:Iteration`および`:Stop`の辞書エントリを呼び出し、これらの記録をリセットします。

デフォルトでは、`RecordAction`はその値を`recorded_values`というフィールドに記録するものと見なされ、これは記録された値の`Vector`です。[`get_record`](@ref get_record(r::RecordAction))`(ra)`を参照してください。
