```
put_assets_into_blocks_by_trading_frequency(
   ts::SortedDataFrame,
   obs_multiple_for_new_block::Real,
   func::Symbol,
   optional_parameters::NamedTuple = NamedTuple(),
)
```

これは、共分散行列をブロック単位で推定する方法を説明するDataFrameを作成します。

### 入力

  * `ts` - ティックデータ。
  * `obs_multiple_for_new_block` - 新しいブロックを作成する前に必要なティックの相対数。したがって、これが1.2である場合、これは1つの資産が前のブロックで最も遅く取引された資産よりも20％以上のティックを持つときに新しいグループが作成されることを意味します。
  * `func` - 使用する共分散推定関数を表すシンボル。
  * `optional_parameters` - `func`関数で使用されるオプションのパラメータ。

### 戻り値

  * 推定がどのように行われるべきかを表す`DataFrame`。`DataFrame`内の行の順序は、推定の順序を示します。

### 参考文献

Hautsch, N., Kyj, L.M. and Oomen, R.C.A. (2012), A blocking and regularization approach to high‐dimensional realized covariance estimation. J. Appl. Econ., 27: 625-645
