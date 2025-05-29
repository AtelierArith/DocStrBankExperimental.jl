dhtrans - デナビット・ハーテンバーグ行列を計算します

この関数は、関節角、長さ、関節オフセット、およびツイストのリンクパラメータが与えられたときに、ロボットアームリンクのデナビット・ハーテンバーグ行列を表す4x4同次変換行列を計算します。

```
Usage: T = dhtrans(theta, offset, length, twist)
 
Arguments:  theta - 関節角（ローカルz軸まわりの回転）
           offset - オフセット（z軸に沿った変換）
           length - リンクx軸に沿った変換
            twist - リンクx軸まわりの回転

Returns:        T - 4x4 同次変換行列。
```

参照: trans(), rotx(), roty(), rotz(), invht()
