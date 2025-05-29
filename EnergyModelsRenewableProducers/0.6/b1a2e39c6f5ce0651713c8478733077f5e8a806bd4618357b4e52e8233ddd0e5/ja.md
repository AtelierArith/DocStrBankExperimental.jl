```
NonDisRES <: AbstractNonDisRES
```

非可調整再生可能エネルギー源です。生産に対応するプロファイルを含むことで、既存の `RefSource` ノードを拡張します。プロファイルは戦略的レベルでの変動を持つことができます。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`profile::TimeProfile`** は、その時点での設置容量の比率としての各運用期間における電力生産です。
  * **`opex_var::TimeProfile`** は生産されたエネルギー単位あたりの変動運営費用です。
  * **`opex_fixed::TimeProfile`** は固定運営費用です。
  * **`output::Dict{Resource, Real}`** は生成された `Resource` で、通常は電力です。
  * **`data::Vector{Data}`** は追加データ（例：投資用）です。フィールド `data` はコンストラクタの使用によって条件付きです。
