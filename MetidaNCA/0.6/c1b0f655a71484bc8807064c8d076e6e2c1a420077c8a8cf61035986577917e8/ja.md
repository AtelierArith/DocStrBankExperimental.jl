```
nca!(data::PKSubject{T,O}; adm = :ev, calcm = :lint, intpm = nothing,  partials = nothing, prtext = :err, verbose = 0, warn = true, io::IO = stdout, modify! = nothing) where T where O
```

  * `adm` - 管理:

      * `:ev` - 血管外;
      * `:iv` - 血管内ボーラス;
  * `calcm` - AUC/AUMC計算方法:

      * `:lint` - 線形台形法;
      * `:luld` - 線形上昇対数下降;
      * `:luldt` - Tmax後の線形上昇対数下降;
      * `:logt` - Tmax後の対数台形法（推奨されません）;
  * `intpm` - 補間方法:

      * `:lint` - 線形台形法;
      * `:luld` - 線形上昇対数下降;
      * `:luldt` - Tmax後の線形上昇対数下降;
      * `:logt` - Tmax後の対数台形法;
      * `:calcm` - `calcm`と同じ;
  * `partials` - 時間間隔のベクトルに対する部分AUCを計算する（`:err`（デフォルト） - 終了時間 > 最後の観察時間の場合はエラーをスロー; `:last` - 外挿なし; `:extr` - `Kel`が計算された場合は外挿を使用、または`Kel`がない場合は`NaN`）;
  * `prtext` - 部分AUCの外挿ルール;
  * `verbose` - `io`に出力、1: 部分面積テーブル、2: 1および結果;
  * `warn` - 警告を表示;
  * `io` - 出力ストリーム;
  * `modify!` - 出力パラメータを修正する関数、`modify!(ncaresult)`を呼び出す（定義されている場合）。

結果:

  * Cmax
  * Tmax
  * Cdose
  * Tlag
  * Clast
  * AUClast
  * AUMClast
  * AUCall
  * Rsq
  * ARsq
  * Kel
  * HL
  * LZint
  * NpLZ
  * Clast_pred
  * AUCinf
  * AUCinf_pred
  * AUMCinf
  * AUMCinf_pred
  * AUCpct
  * MRTlast
  * MRTinf
  * MRTinf_pred
  * Cllast
  * Clinf
  * Vzlast
  * Vzinf
  * Vssinf

定常状態パラメータ（tau使用）:

  * AUCtau
  * AUMCtau
  * Ctau
  * Cavg
  * Ctaumin
  * Accind
  * Fluc
  * Fluctau
  * Swing
  * Swingtau
  * MRTtauinf
  * Cltau
  * Vztau

`partials`はベクトルのベクトル、タプル、またはペアです。例: `partials = [(1,2), (3,4)]`, `partials = [[1,2], (3,4)]`
