```
track_blobs(bt::BlobTracker, vid; display=false, recorder=nothing, threads=Threads.nthreads() > 1, ignoreempty=false)
```

ブロブ追跡のメインエントリーポイント

# 引数:

  * `bt`: BlobTracker
  * `vid`: 画像を反復する何らかの反復可能なもの
  * `display = Base.display`: 画像をライブで表示するための関数。ライブ表示は少し遅くなります。何も表示しない場合は `display=nothing` を使用してください。また、`c = imshow(img); displayfun = img -> imshow!(c["gui"]["canvas"],img);` も考慮してください。
  * `recorder`: 各フレームをディスク上のビデオに記録できるオプションの `Recorder`。記録することはあまり遅くならず、メモリ使用量にもあまり影響しません。
  * `threads`: フレームのスレッド処理を使用しますか？ Juliaが複数のスレッドで起動されている場合にのみ有用です。
  * `ignoreempty=false`: ブロブや測定値を含まないフレームの表示と記録を無視するかどうか。
