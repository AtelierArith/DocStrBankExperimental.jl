使用されなくなったHTTP/1.1チャンクのデータに対して呼び出されます。これは常にHTTP接続のイベントループスレッドで呼び出されます。

# 引数

  * `stream`: このチャンクが送信されたHTTPストリーム。
  * `error_code`: error*codeがAWS*ERROR*SUCCESS (0)の場合、データは正常に送信されました。それ以外のerror*codeは、HTTPストリームが終了処理中であることを示します。error*codeがAWS*ERROR*HTTP*STREAM*HAS*COMPLETEDの場合、ストリームの終了はこのチャンクとは関係ありません。他の非ゼロのエラーコードは、この特定のチャンクのデータに問題があることを示します。
  * `user_data`: このチャンクのユーザーデータ。
