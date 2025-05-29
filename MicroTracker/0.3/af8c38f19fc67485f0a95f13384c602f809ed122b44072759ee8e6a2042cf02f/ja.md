```
loadframe(vidname::AbstractString, framenumber::Integer)
```

`vidname`のビデオ内の`framenumber`フレームに対応する画像を返します。`original_video`フォルダーに存在する必要があります。

自動的に名前が付けられたtifsの方式を見て、パターンに一致させます。**必ずしも**データ内の実際のフレーム番号と一致するわけではなく、特に最初のフレームに粒子がない場合はそうです。

通常、ImageJの画像は0からインデックス付けされ、Juliaは1からインデックス付けされます。したがって、この関数は`framenumber-1`で名前付けされた画像を返します。
