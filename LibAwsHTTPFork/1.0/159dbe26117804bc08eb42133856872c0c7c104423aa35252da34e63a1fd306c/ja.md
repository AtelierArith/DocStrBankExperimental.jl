出力されるHTTP2データフレームのデータがもはや使用されていないときに呼び出されます。これは常にHTTP接続のイベントループスレッドで呼び出されます。

# 引数

  * `stream`: この書き込みが送信されたHTTP2ストリーム。
  * `error_code`: error*codeがAWS*ERROR*SUCCESS (0)の場合、データは正常に送信されました。それ以外のerror*codeは、HTTPストリームが終了処理中であることを示します。error*codeがAWS*ERROR*HTTP*STREAM*HAS*COMPLETEDの場合、ストリームの終了はこの書き込みとは関係ありません。それ以外の非ゼロのエラーコードは、この特定の書き込みのデータに問題があることを示します。
  * `user_data`: この書き込みのユーザーデータ。
