タスクがDeviceDefenderタスクを実行中にエラーが発生したことを報告するための一般的なコールバックハンドラー。エラーコードは、失敗がどこで、いつ、どのように発生したかを説明するには限界があるため、ここでのエラーは、どこで、いつ、どのように発生したかを最もよく伝えることができ、基盤となる呼び出しの詳細はログ出力に見つけるべきです。

# 引数

  * `is_task_stopped`:[in] タスクが実行を続けられないかどうかを示すフラグ
  * `error_code`:[in] 失敗の性質を説明するエラーコード
