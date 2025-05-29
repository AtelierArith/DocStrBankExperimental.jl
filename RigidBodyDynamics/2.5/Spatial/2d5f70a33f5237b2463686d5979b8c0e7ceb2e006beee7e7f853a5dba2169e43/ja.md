`CartesianFrame3D` `f1` が `f2s` のいずれかであることを確認します。

`f2s` が `CartesianFrame3D` の場合、`f1` と `f2s` は単に等価性がチェックされます。

境界チェックが有効な場合、`f1` が `f2s` に含まれていないときは `ArgumentError` がスローされます。境界チェックが無効な場合、`@framecheck` は何もしません。
