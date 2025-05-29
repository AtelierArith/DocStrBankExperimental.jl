接続試行が成功またはエラーで完了したときに呼び出されます。

エラーコードが AWS*ERROR*SUCCESS の場合、サーバーから CONNACK が受信され、return*code と session*present には受信した値が含まれます。エラーコードが AWS*ERROR*SUCCESS でない場合、それは接続中に発生した内部エラーを指し、return*code と session*present は無効です。
