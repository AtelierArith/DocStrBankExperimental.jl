```
RoundingSettings(settings...)
```

丸め手順の設定：

1. カーネルの発見

      * `kernel_errbound`: (デフォルト: `1e-10`) カーネルベクトルの許容誤差。つまり、Xvの最大エントリは絶対値でこの値以下である必要があります。
      * `kernel_round_errbound`: (デフォルト: `1e-15`) 簡約行列のエントリごとの丸め時に許可される最大誤差
      * `kernel_use_primal`: (デフォルト: `true`) カーネルベクトルを見つけるために原始解を使用する（そうでない場合は、双対解のSVDを使用）
      * `kernel_lll`: (デフォルト: `false`) trueの場合、カーネルのヌル空間を見つけるためにLLLアルゴリズムを使用します。そうでない場合は、カーネルベクトルを見つけるために簡約行列を使用します。
      * `kernel_bits`: (デフォルト: `1000`) LLLアルゴリズムで使用される最大ビット数（関係を見つけるためまたはRREFのエントリを見つけるため）
2. カーネルベクトルの削減

      * `reduce_kernelvectors`: (デフォルト: `true`) 削減ステップを適用するかどうか
      * `reduce_kernelvectors_cutoff`: (デフォルト: `400`) サイズがこのカットオフ以下の場合、フルマトリックスで削減を行います。それ以外の場合はサブマトリックスで行います。
      * `reduce_kernelvectors_stepsize`: (デフォルト: `200`) 削減ステップの各反復で考慮する追加の列の数
3. 問題と解の変換

      * `unimodular_transform`: (デフォルト: `true`) 削減ステップで得られたユニモジュラー変換を使用
      * `normalize_transformation`: (デフォルト: `true`) 問題の整数変換を得るために対角行列で乗算します（QQ上の問題用）
4. フィールド内での近似解の発見

      * `regularization`: (デフォルト: `1e-20`) 拡張システムを解くためにこの正則化を使用
      * `approximation_decimals`: (デフォルト: `40`) この桁数を使用して数値解をエントリごとに近似
5. 制約のアフィン空間への解の丸め

      * `redundancyfactor`: (デフォルト: `10`) 潜在的なピボットとして制約列の数の少なくともこの倍数を取る
      * `pseudo`: (デフォルト: `true`) 丸めのために擬似逆行列を使用（これにより、必要以上に大きなビットサイズの解が得られる場合があります）
      * `pseudo_columnfactor`: (デフォルト: `1.05`) r行のシステムの場合、擬似逆行列のためにr * pseudo_columnfactorの列数を使用
      * `extracolumns_linindep`: (デフォルト: `false`) trueの場合、互いに線形独立な追加の列を取る（そうでない場合はランダムな列）
