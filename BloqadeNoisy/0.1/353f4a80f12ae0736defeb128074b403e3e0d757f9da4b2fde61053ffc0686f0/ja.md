```
struct NoisySchrodingerEquation
```

シュレディンガー方程式のデコレータオブジェクト。標準的なODE問題に適合するためにf(dstate, state, p, t)インターフェースを実装します。

# 引数

  * `equation`: 問題のためのコヒーレントな'SchrodingerEquation`方程式
  * `imag_evo`: 非エルミート部分のハミルトニアンを定義する崩壊演算子Lのための∑_L L^†L
  * `num_cops``: 崩壊演算子の数（表示用）
