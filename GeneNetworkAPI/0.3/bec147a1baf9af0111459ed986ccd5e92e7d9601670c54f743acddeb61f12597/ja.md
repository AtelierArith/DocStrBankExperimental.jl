```
function run_rqtl(dataset::String, trait::String; method::String="hk",
              model::String="normal", n_perm::Int64=0,
              control_marker::String="",
              gn_url::String=gn_url())
```

指定された `dataset` における指定された `trait` で R/qtl の `scanone` 関数を実行します。

いくつかのオプション引数は、親の `scanone` 関数のオプションに類似しています。詳細は [その関数のヘルプ](https://rqtl.org/manual/qtl-manual.pdf) を参照してください。

オプション引数には以下が含まれます：

  * method (デフォルト="hk"): 可能な値は

      * hk: Haley-Knott 法
      * em: EM アルゴリズム
      * ehk: 拡張 EM アルゴリズム
      * imp: 多重代入
      * mr: 欠損遺伝子型を持つ個体を除外したマーカー回帰
      * mr-imp: 単一代入で欠損データを埋めるマーカー回帰
      * mr-argmax: ビタビアルゴリズムで埋めるマーカー回帰
  * model (デフォルト="normal"): 遺伝子型に基づく trait のモデル; 可能な値は

      * normal: 完全データに対する線形回帰に相当
      * binary: 完全データに対するロジスティック回帰に相当
      * 2part: 遺伝子型に基づく trait の二部モデル
      * np: ノンパラメトリック分析
  * n_perm (デフォルト=0) 実行する置換の数
  * control_marker: 加法的共変量として制御するマーカーの名前
