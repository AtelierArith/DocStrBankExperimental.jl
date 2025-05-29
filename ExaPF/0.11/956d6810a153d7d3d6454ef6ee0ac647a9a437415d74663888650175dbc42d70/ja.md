```
run_pf(
    polar::PolarForm, stack::NetworkStack;
    rtol=1e-8, max_iter=20, verbose=0,
)
```

スタック $x$ に関して、電力フロー方程式 $g(x, u) = 0$ を解きます。初期状態 $x$ は `stack` 内に暗黙的に指定されており、極形式に関連付けられた [`mapping`](@ref) があります。オブジェクト `stack` は関数内でインプレースで変更されます。

アルゴリズムは、許容誤差 `rtol` または最大反復回数 `maxiter` に達したときに停止します。

### 引数

  * `polar::AbstractFormulation`: 電力フロー方程式の定式化
  * `stack::NetworkStack`: ネットワーク内の初期値

### 例

```jldoctest; setup=:(using ExaPF)
julia> polar = ExaPF.load_polar("case9");

julia> stack = ExaPF.NetworkStack(polar);

julia> conv = run_pf(polar, stack);

julia> conv.has_converged
true

julia> conv.n_iterations
4
```
