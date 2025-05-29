```
struct NoisySchrodingerEquation
NoisySchrodingerEquation(reg, tspan, hamiltonian, c_ops; kw...)
NoisySchrodingerEquation(reg, tspan, hamiltonian, noise_model; kw...)
```

オープンシステムにおける単一のノイズのある軌跡を弱結合限界で表すODE問題を定義します

# 引数

  * `reg`: 問題の進化レジスタと初期状態
  * `tspan`: シミュレーションを保存する時間のベクトル
  * `hamiltonian`: 進化ハミルトニアンを表す`rydberg_h`によって生成されるAbstractBlock
