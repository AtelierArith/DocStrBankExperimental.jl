クランク・ニコルソン二段階、2次のメソッドの表

```julia
TableauCrankNicolson(::Type{T}=Float64) where {T}
```

コンストラクタは1つのオプション引数を取ります。それは表の要素型です。

参考文献:

```
J. Crank and P. Nicolson.
A practical method for numerical evaluation of solutions of partial differential equations of the heat-conduction type.
Mathematical Proceedings of the Cambridge Philosophical Society, Volume 43, Issue 1, Pages 50-67, 1947.
doi: 10.1017/S0305004100023197
```
