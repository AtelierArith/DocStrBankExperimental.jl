create_entity!(w::Workflow)

  * ref_versionによって識別されるバイテンポラルトランザクションを開きます
  * 履歴、バージョン、有効期間、およびWorkflowを永続化します
  * 必要条件: w.tsw_validfromは有効な日付である必要があります
