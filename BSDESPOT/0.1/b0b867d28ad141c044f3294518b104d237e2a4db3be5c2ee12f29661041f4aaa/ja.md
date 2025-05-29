```
DefaultPolicyLB(policy; max_depth=nothing, final_value=(m,x)->0.0)
DefaultPolicyLB(solver; max_depth=nothing, final_value=(m,x)->0.0)
```

信念内のシナリオでデフォルトポリシーを実行することによって計算された下限。

# キーワード引数

  * `max_depth::Union{Nothing,Int}=nothing`: シミュレーションを実行する最大深さ。信念の深さは自動的に引かれるため、下限のためのシミュレーションは `max_depth-b.depth` ステップで実行されます。`nothing` の場合、ソルバーの最大深さが使用されます。
  * `final_value=(m,x)->0.0`: シミュレーションの最後に `max_depth` に達したときに追加される値を指定する関数（または呼び出し可能なオブジェクト）。この関数は、`POMDP` と `ScenarioBelief` の2つの引数で呼び出されます。信念内の状態が終端である場合には呼び出されません。
