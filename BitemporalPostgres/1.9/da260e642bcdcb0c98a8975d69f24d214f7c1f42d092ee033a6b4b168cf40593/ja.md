update_entity!(w::Workflow)

  * ref_versionによって識別されるバイテンポラルトランザクションを開きます
  * バージョン、validityInterval、およびWorkflowを永続化します
  * 回顧的トランザクションの場合

      * シャドウバージョンからのすべての挿入および変異を予備的に無効化します
      * シャドウバージョンによって無効化されたすべての改訂を予備的に復活させます
  * 必要条件:

      * w.tsw_validfromは有効な日付であること
      * w.ref_historyは有効な履歴IDであること
      * w.ref*versionはw.ref*historyの有効なバージョンであること
