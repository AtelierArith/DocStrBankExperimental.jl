可変構造体は、FMUの実行構成を表します。`fmi2Reset`や`fmi2FreeInstance`の呼び出しに問題があるFMUにとって、これは非常に便利です。

# フィールド

  * `terminate::Bool`: 各トレーニングステップ/シミュレーションの前に`fmi2Terminate`を呼び出します。
  * `reset::Bool`: 各トレーニングステップ/シミュレーションの前に`fmi2Reset`を呼び出します。
  * `setup::Bool`: 各トレーニングステップ/シミュレーションの前にセットアップ関数を呼び出します。
  * `instantiate::Bool`: 各トレーニングステップ/シミュレーションの前に`fmi2Instantiate`を呼び出します。
  * `freeInstance::Bool`: 各トレーニングステップ/シミュレーションの後に`fmi2FreeInstance`を呼び出します。
  * `loggingOn::Bool`: ロギングを有効または無効にします。
  * `externalCallbacks::Bool`: 外部コールバックを使用します。
  * `force::Bool`: 強制アクションのデフォルト値。
  * `handleStateEvents::Bool`: シミュレーション/トレーニング中に状態イベントを処理します。
  * `handleTimeEvents::Bool`: シミュレーション/トレーニング中に時間イベントを処理します。
  * `assertOnError::Bool`: `fmi2XXX`コマンドが失敗した場合に例外がスローされるかどうか（>= `fmi2StatusError`）。
  * `assertOnWarning::Bool`: `fmi2XXX`コマンドが警告を出した場合に例外がスローされるかどうか（>= `fmi2StatusWarning`）。
  * `autoTimeShift::Bool`: 0.0から始まらないシミュレーション間隔のために、すべての時間関連関数をシフトするかどうか。
  * `inplace_eval::Bool`: FMU/コンポーネントの評価がインプレースで行われるべきかどうか。
  * `sensealg::Any`: 解決呼び出しに対する感度推定のためのアルゴリズム（[ToDo] データ型/なし）。
  * `rootSearchInterpolationPoints::UInt`: ルート検索補間点の数。
  * `useVectorCallbacks::Bool`: ベクトル（高速）またはスカラー（低速）コールバックを使用するかどうか。
  * `maxNewDiscreteStateCalls::UInt`: 例外をスローする前の`fmi2NewDiscreteStates`の最大呼び出し回数。
  * `maxStateEventsPerSecond::UInt`: 1秒あたりに発生する最大状態イベント（それ以上はイベントのチャタリングと解釈されます）。
  * `snapshotDeltaTimeTolerance::Float64`: スナップショットを区別するための距離。
  * `eval_t_gradients::Bool`: 時間勾配∂ẋ/∂tおよび∂y/∂tをサンプリングするべきかどうか（FMI標準の一部ではありません）。
  * `JVPBuiltInDerivatives::Bool`: ジャコビアンをキャッシュせずにFMU上のJVP感度のために組み込みの方向微分を使用します（これはFMU内で行われますが、デフォルトではありません）。
  * `VJPBuiltInDerivatives::Bool`: ジャコビアンをキャッシュせずにFMU上のVJP感度のために組み込みの随伴微分を使用します（これはFMU内で行われますが、デフォルトではありません）。
  * `sensitivity_strategy::Symbol`: ジャコビアン/勾配の構築戦略、利用可能なオプションは`:FMIDirectionalDerivative`、`:FMIAdjointDerivative`、`:FiniteDiff`です。
  * `set_p_every_step::Bool`: 各シミュレーションステップでパラメータが設定されるかどうか - これは一般的ではなく、パラメータは通常、初期化中/後に一度だけ設定されます。
  * `concat_eval::Bool`: （非推奨）FMU/コンポーネントの評価がタプル`(y, dx, ec)`を返すべきか、連結`[y..., dx..., ec...]`を返すべきか。
