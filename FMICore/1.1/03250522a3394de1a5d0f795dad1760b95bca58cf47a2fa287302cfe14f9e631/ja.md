ソース: FMISpec2.0.2[p.23]: 2.1.6 FMUの初期化、終了、およびリセット

FMUに実験を設定するよう指示します。この関数は、fmi2Instantiateの後、fmi2EnterInitializationModeが呼び出される前に呼び出す必要があります。この関数は、ロガー関数コールバックを介して出力されるデバッグログの制御を行います。loggingOn = fmi2Trueの場合、デバッグログが有効になり、それ以外の場合はオフになります。
