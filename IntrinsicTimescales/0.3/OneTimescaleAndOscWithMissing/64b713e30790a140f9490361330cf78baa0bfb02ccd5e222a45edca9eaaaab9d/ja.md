```
int_fit(model::OneTimescaleAndOscWithMissingModel, param_dict=nothing)
```

指定されたフィッティングメソッドを使用して推論を行います。

# 引数

  * `model::OneTimescaleAndOscWithMissingModel`: モデルインスタンス
  * `param_dict=nothing`: アルゴリズムパラメータのオプション辞書。何も指定しない場合はデフォルトを使用します。

# 戻り値

ABCメソッドの場合:

  * `posterior_samples`: 受け入れられたパラメータサンプルの行列
  * `posterior_MAP`: 最大事後推定
  * `abc_record`: ABCイテレーションの完全な記録

ADVIメソッドの場合:

  * `ADVIResults`: サンプル、MAP推定、分散、および完全なチェーンを含むコンテナ

# 注意事項

  * ABCの場合: 適応的エプシロン選択を用いた人口モンテカルロABCを使用
  * ADVIの場合: Turing.jlを介した自動微分変分推論を使用
  * パラメータ辞書は各メソッドに合わせてカスタマイズ可能です（get*param*dict_abc()を参照）。
