```
Scene(movie, function, range;
    easingfunction=easinoutquad,
    optarg=nothing)
```

Scene() コンストラクタ関数を使用してシーンを作成します。ムービー、シーンを生成する関数、およびフレームの範囲を指定します。オプションで、イージング関数やその他の情報を `optarg` に供給することができ、これは `scene.opts` としてアクセスできます。

### 例

```julia
function initial(scene, framenumber)
    balls = scene.opts
    ...
end

animate(poolmovie, [
    Scene(poolmovie, initial, optarg=balls, 1:20),
    ...
    ])
```

フレーム生成関数内でイージング関数を使用するには、例えば次のように正規化された値を作成できます：

```julia
eased_n = scene.easingfunction(framenumber, 0, 1, scene.framerange.stop)
```

または、シーンがフレーム1から始まらない場合は、次のように正規化されたイージング関数を計算します：

```julia
eased_n = scene.easingfunction(framenumber - scene.framerange.start,
    0, 1, scene.framerange.stop - scene.framerange.start)
```
