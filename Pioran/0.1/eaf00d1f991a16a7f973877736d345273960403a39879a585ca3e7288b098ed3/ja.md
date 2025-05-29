```
CARMA(p, q, rα, β, σ²)
```

連続時間自己回帰移動平均 (CARMA) モデルのパワースペクトル密度

  * `p`: 自己回帰多項式の次数
  * `q`: 移動平均多項式の次数
  * `rα`: 自己回帰多項式の根の長さ p+1
  * `β`: 移動平均係数の長さ q+1
  * `σ²`: プロセスの分散

CARMA モデルのパワースペクトル密度は次のように与えられます：

$$
\mathcal{P}(f) = \sigma^2 \left|\dfrac{\sum\limits_{k=0}^q \beta_k \left(2\pi\mathrm{i}f\right)^k }{\sum\limits_{l=0}^p \alpha_l \left(2\pi\mathrm{i}f\right)^l}\right|^2
$$
