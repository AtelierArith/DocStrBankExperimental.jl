@api <cmd> [<symbols>...]

  * freeze                # モジュールの最後でAPIをフリーズするために使用
  * list     <modules>... # 指定されたモジュールのAPIをリストする（指定がない場合は現在のモジュール）
  * use      <modules>... # インポートせずに使用する（すなわち拡張できない）
  * use!     <modules>... # インポートせずに使用する（すなわち拡張できない）、"export"
  * test     <modules>... # 公開および開発APIを使用して、テスト目的で
  * extend   <modules>... # 開発用、api & devをインポートし、api & dev定義を使用
  * extend!  <modules>... # 開発用、api & devをインポートし、api & dev定義を使用、"export"
  * reexport <modules>... # それらのモジュールから公開定義をエクスポート
  * base     <names...>   # APIの一部であるBaseから関数を追加（拡張可能）
  * base!    <names...>   # Baseから関数を追加するか、Baseにない場合は定義する
  * public   <names...>   # 公開APIの一部である他のシンボルを追加（構造体、定数）
  * public!  <names...>   # 公開APIの一部である関数を追加（拡張可能）
  * develop  <names...>   # 開発APIの一部である他のシンボルを追加
  * develop! <names...>   # 開発APIの一部である関数を追加（拡張可能）
  * define!  <names...>   # 拡張される関数を定義する、公開API
  * defdev!  <names...>   # 拡張される関数を定義する、開発API
  * modules  <names...>   # APIの一部であるサブモジュール名を追加
  * path     <paths...>  # LOAD_PATHにパスを追加
  * def <name> <expr>    # @defマクロと同じ、指定された名前のマクロを作成
