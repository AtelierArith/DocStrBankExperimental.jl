`AbstractGridArray`のサブタイプで、極に向かって経度点の数が減少したリンググリッドの配列です。つまり、これらは「完全」ではなく、`AbstractFullGridArray`を参照してください。これらのグリッド上のデータは行列として表現できず、0から360˚Eまで、北から南へ、リングごとに順序付けられたベクトルに展開する必要があります。減少したグリッドの例としては、八面体ガウスグリッドやクレンズホーグリッド、HEALPixグリッドがあります。
