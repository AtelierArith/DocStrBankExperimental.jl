```
拡散過程の無限小生成子の離散化されたバージョンを返します

    𝕋: f ⭌ lim 1/t * E[f(x_t)|x_0=x]
             = μx * ∂f + 0.5 * σx^2 * ∂^2f

状態空間の境界で

    ∂f(x) = 0 

となる関数 f の集合上で定義されています

この演算子の転置は次のように対応します
    
    𝕋': g ⭌ v * g - ∂(μx * g) + 0.5 * ∂^2(σx^2 * g)

状態空間の境界で

    -μx * g(x) + 0.5 * ∂(σx^2 * g) = 0

となる関数 g の集合上で定義されています
```
