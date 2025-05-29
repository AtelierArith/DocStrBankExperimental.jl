```
pair_mix(g,P::ClapeyronParam,Q::ClapeyronParam)::PairParam
pair_mix(g,P::ClapeyronParam,Q::ClapeyronParam)::PairParam
```

ペアと単一パラメータの一般的な組み合わせルール。非対角エントリが次のように等しいペアパラメータ `P` を返します：

```
Pᵢⱼ = g(Pᵢ,Pⱼ,Qᵢ,Qⱼ,Qᵢⱼ)
```

ここで `f` は次のルールに従う「組み合わせ」関数です：

```
Pᵢⱼ = Pⱼᵢ = g(Pᵢ,Pⱼ,Qᵢ,Qⱼ,Qᵢⱼ) = g(Pⱼ,Pᵢ,Qⱼ,Qᵢ,Qᵢⱼ)
g(Pᵢ,Pᵢ,Qᵢ,Qᵢ,Qᵢ) = Pᵢ
```

これは `kij_mix` のより一般的な形式であり、`kij_mix(f,P,Q) == pair_mix(g,P,Q)` が正しいのは次の条件を満たす場合です：

```
f(Pᵢ,Pⱼ,Qᵢⱼ) = g(Pᵢ,Pⱼ,_,_,Qᵢⱼ)

`Q` に `SingleParam` またはベクトルを入力として渡すと、`Qᵢⱼ` は 0 と見なされます。
```
