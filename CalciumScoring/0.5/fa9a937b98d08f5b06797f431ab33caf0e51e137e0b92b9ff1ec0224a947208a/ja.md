## `score` (統合)

```julia
score(S_Bkg, S_Obj, algorithm::Integrated)

score(S_Bkg, S_Obj, size, algorithm::Integrated)

score(S_Bkg, S_Obj, size, ρ, algorithm::Integrated)
```

統合強度アプローチを使用して、`vol` に含まれるオブジェクトボクセル/体積/質量の合計を求めます。

関数は異なるパラメータで呼び出すことができます：

1. `S_Bkg`, `S_Obj`, `algorithm` - オブジェクトボクセルの合計数を返します。
2. `S_Bkg`, `S_Obj`, `size`, `algorithm` - オブジェクトの合計体積を返します。
3. `S_Bkg`, `S_Obj`, `size`, `ρ`, `algorithm` - オブジェクトの合計質量を返します。

#### 入力

  * `S_Bkg`: `vol` における純背景信号強度
  * `S_Obj`: `vol` における純オブジェクト信号強度
  * `size`: （オプション）指定された `vol` におけるボクセルのサイズ（2番目と3番目のバリエーションのみ）
  * `ρ`: （オプション）`vol` に含まれる対象オブジェクトの密度（3番目のバリエーションのみ）
  * `algorithm`: ノイズと部分体積効果を考慮し、全体の体積 `vol` の強度を統合する `Integrated` アルゴリズム

#### 参考文献

[冠動脈カルシウム質量測定のための統合強度ベースの技術：ファントム研究](https://doi.org/10.1002/mp.16326)

[CT血管造影を用いた血管断面積の正確な定量化：シミュレーション研究](https://doi.org/10.1007/s10554-016-1007-9)
