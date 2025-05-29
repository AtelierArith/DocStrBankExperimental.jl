```
SortedParticleList{N,M,T<:Unsigned}
```

スパースフォック状態を格納するための型。各粒子のモード番号をエントリとして格納し、そのモードのみが保存されます。エントリは常にソートされた状態で保持されます。

`SortedParticleList`を反復処理すると、占有モードが占有数、モード番号、およびリスト内の位置のタプルとして得られます。

# コンストラクタ

  * `SortedParticleList{N,M,T}(::SVector{N,T})`: 安全でないコンストラクタ。入力をソートしません。
  * `SortedParticleList(arr::AbstractVector)`: ONRを`SortedParticleList`に変換します。
