`WFST(isym, [osym]; W = TropicalWeight{Float32})`

空の重み付き有限状態遷移器 (WFST) を構築します。

  * `isym` 入力シンボルテーブル（辞書またはベクターであることができます）
  * `osym` 出力シンボル辞書（オプション）
  * `W` 重みの型

シンボルテーブルが `AbstractDict{I,D}` の場合、`D` は整数でなければならず、`I` はシンボルの型です。
