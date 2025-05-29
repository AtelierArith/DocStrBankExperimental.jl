```
jacobian(::ReverseMode, f, x; n_outs=nothing, chunk=nothing)
jacobian(::ReverseMode, f, x)
```

配列出力関数 `f` のヤコビアンを（潜在的にベクトル）逆モードを使用して計算します。`chunk` 引数はオプションで使用するチャンクサイズを示し、`n_outs` はオプションで `f` によって返される配列の形状を示します（例: `size(f(x))`）。

例:

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

jacobian(Reverse, f, [2.0, 3.0, 4.0])

# 出力
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(ReverseWithPrimal, f, [2.0, 3.0, 4.0])

# 出力
(derivs = ([3.0 2.0 0.0; 0.0 1.0 1.0],), val = [6.0, 7.0])
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(Reverse, f, [2.0, 3.0, 4.0], n_outs=Val((2,)))

# 出力
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(ReverseWithPrimal, f, [2.0, 3.0, 4.0], n_outs=Val((2,)))

# 出力
(derivs = ([3.0 2.0 0.0; 0.0 1.0 1.0],), val = [6.0, 7.0])
```

この関数は、形状が `(size(output)..., size(input)...)` の AbstractArray を返します。この関数によって返される AbstractArray の型については、現在のところ保証はありません（提供された場合、入力の AbstractArray と同じである場合もあれば、そうでない場合もあります）。

将来的には、この関数が非配列戻り型を処理するように拡張されると、入力型の値の形状 `size(output)` の AbstractArray を返すようになります。```
