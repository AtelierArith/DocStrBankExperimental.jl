```
srs(base_acc::ArbitraryExc, freq, t, ξ = 0.05,
    type = (instance = :primary, amplitude = :abs), alg = :Smallwood)
```

ショック応答スペクトル (SRS) を計算します

**入力**

  * `base_acc::ArbitraryExc`: 基準加速度タイプ - 詳細は `excitation` 関数を参照
  * `freq`: 周波数のベクトル [Hz]
  * `t`: 応答を評価する時間点
  * `ξ`: 減衰比 (デフォルト = 0.05)
  * `type`: SRSのタイプ

      * `instance`: SRSのインスタンス

          * `:primary`: プライマリインスタンス (デフォルト)
          * `:secondary`: セカンダリインスタンス
      * `amplitude`: SRS計算に使用される振幅

          * `:abs`: 最大絶対振幅 (デフォルト)
          * `:pos`: 最大正振幅
          * `:neg`: 最大負振幅
  * `alg`: SRSを計算するためのアルゴリズム

      * `:Basic`: 基本アルゴリズム
      * `:RecursiveInt`: 再帰的積分アルゴリズム
      * `:RecursiveFilt`: 再帰的フィルタリングアルゴリズム
      * `:Smallwood`: スモールウッドアルゴリズム (デフォルト)

**出力**

  * `srs`: SRS値のベクトル

*注*

  * プライマリインスタンス - 基準加速度の適用中のシステムの応答
  * セカンダリインスタンス - 基準加速度の適用後のシステムの応答
