```
change_independent_variable(
    sys::AbstractODESystem, iv, eqs = [];
    add_old_diff = false, simplify = true, fold = false
)
```

ODEシステム`sys`の独立変数（例：$t$）を従属変数`iv`（例：$u(t)$）に変換します。この変換は、新しい独立変数と古い独立変数の間のマッピングが一対一であるときに明確に定義されます。これは、一方が他方の厳密に増加する関数である場合（例：$du(t)/dt > 0$または$du(t)/dt < 0$）に満たされます。

新しい独立変数と古い独立変数に関する追加の方程式`eqs`は、変換に考慮されます。

# キーワード引数

  * `add_old_diff`: 新しい独立変数を用いて古い独立変数の微分方程式を追加するかどうか。逆関数の法則$dt/du = 1/(du/dt)$を使用します。
  * `simplify`: 拡張された導関数の表現が簡略化されるかどうか。これにより、より整然とした変換が得られます。
  * `fold`: 内部の置換が数値表現を評価するかどうか。

# 構造的簡略化前の使用法

変数の変更は、構造的簡略化の前に行う必要があります。`structural_simplify`への次の呼び出しでは、ダミー変数間の望ましくない制約方程式を避けるために、`allow_symbolic = true`を渡すことを検討してください。

# 非自律システムでの使用法

`sys`が非自律（すなわち、$t$がその方程式に明示的に現れる）である場合、新しい独立変数と古い独立変数を関連付ける代数方程式（例：$t = f(u(t))$）を渡すことを検討してください。そうしないと、変換されたシステムは過不足になる可能性があります。代数的関係が不明な場合は、代わりに`add_old_diff`を使用することを検討してください。

# 階層システムでの使用法

`iv`は`sys`内の名前空間のない変数であることが推奨されます。これは、トップレベルのシステムに属するか、`GlobalScope`で宣言されたサブシステム内の変数であることを意味します。

# 例

一定の水平速度での自由落下を考えます。物理学は自然に位置を時間の関数として記述します。独立変数を変更することにより、水平位置の関数として垂直位置を再定式化できます：

```julia
julia> @variables x(t) y(t);

julia> @named M = ODESystem([D(D(y)) ~ -9.81, D(D(x)) ~ 0.0], t);

julia> M = change_independent_variable(M, x);

julia> M = structural_simplify(M; allow_symbolic = true);

julia> unknowns(M)
3-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 xˍt(x)
 y(x)
 yˍx(x)
```
