```
状態データ型
```

状態は現在のメタヒューリスティックのステータスを保存するために使用されます。実際、`optimize`関数は`State`を返します。

  * `best_sol` これまでに見つかった最良の解を保存します。
  * `population` は、集団ベースのアルゴリズム用のArray{typeof(best_sol)}です。
  * `f_calls` は目的関数の評価回数です。
  * `g_calls` は不等式制約の評価回数です。
  * `h_calls` は等式制約の評価回数です。
  * `iteration` は現在の反復回数です。
  * `success_rate` は親よりも良い新しい生成された解の割合です。
  * `convergence` は各反復で`State`を保存するために使用されます。
  * `start_time` は最適化プロセスの前に`time()`を保存します。
  * `final_time` は最適化プロセスの後に`time()`を保存します。
  * `stop` がtrueの場合、最適化プロセスを停止します。

# 例

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # 下限
                    10.0  10 10 ] # 上限
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> state = optimize(f, bounds)
+=========== RESULT ==========+
| Iter.: 1009
| f(x) = 7.16271e-163
| solution.x = [-7.691251412064516e-83, 1.0826961235605951e-82, -8.358428300092186e-82]
| f calls: 21190
| Total time: 0.2526 s
+============================+

julia> minimum(state)
7.162710802659093e-163

julia> minimizer(state)
3-element Array{Float64,1}:
 -7.691251412064516e-83
  1.0826961235605951e-82
 -8.358428300092186e-82
```
