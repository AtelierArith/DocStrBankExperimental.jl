```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

モジュール `module` 内のバインディング `name` の値を `x` に設定または変更します。型変換は行われないため、バインディングに対してすでに型が宣言されている場合、`x` は適切な型でなければならず、そうでない場合はエラーが発生します。

さらに、この操作に対して原子的な順序を指定することができ、指定しない場合はデフォルトで単調になります。

ユーザーは通常、この機能に [`setproperty!`](@ref Base.setproperty!) 関数または対応する構文（すなわち `module.name = x`）を通じてアクセスするため、これは非常に特定の使用ケースのために意図されています。

!!! compat "Julia 1.9"
    この関数は Julia 1.9 以降が必要です。


他に [`setproperty!`](@ref Base.setproperty!) と [`getglobal`](@ref) を参照してください。

# 例

```jldoctest
julia> module M end;

julia> M.a  # `getglobal(M, :a)` と同じ
ERROR: UndefVarError: `a` not defined

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```
