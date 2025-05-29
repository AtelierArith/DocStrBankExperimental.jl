```julia
mutable struct Callback{CN, AC}
```

`condition` と `action` から `Callback` を構築します。`condition` と `action` は単一引数の関数でなければなりません。`condition` は、チェックする条件が発生した場合に `true` を返し、そうでない場合は `false` を返します。`action` は、`Callback` が構築された特定のアクションを実行します。`Callback` は、その単一引数を渡すことで呼び出すことができ、これは主に `Callback` にバインドされています。

# フィールド

  * `condition::Any`: コールバックの条件関数。単一引数の関数であることが期待されます
  * `action::Any`: コールバックのアクション。単一引数の関数であることが期待されます
  * `enabled::Bool`: true の場合、コールバックが有効化されます
  * `id::Base.UUID`: 一意の識別子

# 例

```julia
julia> struct Object  # ダミー型を定義します。
       x::Int 
       clb::Callback 
       end

julia> cond(obj) = obj.x > 0;  # コールバック条件を定義します。

julia> action(obj) = println("obj.x = ", obj.x); # コールバックアクションを定義します。

julia> obj = Object(1, Callback(condition=cond, action=action))
Object(1, Callback(condition:cond, action:action))

julia> obj.clb(obj)  # バウンドされた `obj` のコールバックを呼び出します。
obj.x = 1
```
