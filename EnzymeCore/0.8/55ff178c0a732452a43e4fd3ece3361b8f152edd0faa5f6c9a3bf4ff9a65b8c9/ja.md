```
DuplicatedNoNeed(x, ∂f_∂x)
```

[`Duplicated`](@ref) と同様ですが、Enzyme が元の結果を計算せず、導関数の値のみを計算することを指定します。これにより、パフォーマンスの向上の機会が生まれます。

```julia

function square_byref(out, v)
    out[] = v * v
    nothing
end

out = Ref(0.0)
dout = Ref(1.0)
Enzyme.autodiff(Reverse, square_byref, DuplicatedNoNeed(out, dout), Active(1.0))
dout[]

# output
0.0
```

例えば、out 変数を `DuplicatedNoNeed` としてマークすることで、Enzyme は `v * v` の計算を回避できる（導関数は計算し続ける）ようになります。

これは `x` が書き込み専用の変数である場合にのみ使用するべきです。そうでない場合、微分された関数が `x` に値を格納し、その後の計算でそれを読み戻す場合、`DuplicatedNoNeed` を使用すると不正確な導関数が得られる可能性があります。特に、`DuplicatedNoNeed` は事前に割り当てられた作業領域には使用すべきではありません。たとえユーザーが最終的な値を気にしない場合でも、変数を NoNeed としてマークすることは、その変数からの読み取りが未定義になることを意味します。
