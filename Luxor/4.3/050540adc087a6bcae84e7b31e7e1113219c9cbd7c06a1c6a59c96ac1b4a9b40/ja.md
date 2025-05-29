`Movie` と `Scene` タイプおよび `animate()` 関数は、アニメーション GIF またはムービーを作成するために使用できるフレームを作成するのに役立ちます。

1. Movie コンストラクタに幅、高さ、タイトル、およびオプションでフレーム範囲を提供します：

    `julia  demo = Movie(400, 400, "test", 1:500)`
2. 1つ以上のシーンとシーン描画関数を定義します。
3. `animate()` 関数を実行し、それらのシーンを呼び出します。

例

```julia
bang = Movie(400, 100, "bang")

backdrop(scene, framenumber) =  background("black")

function frame1(scene, framenumber)
    background("white")
    sethue("black")
    eased_n = scene.easingfunction(framenumber, 0, 1, scene.framerange.stop)
    circle(O, 40 * eased_n, :fill)
end

animate(bang, [
    Scene(bang, backdrop, 0:200),
    Scene(bang, frame1, 0:200, easingfunction=easeinsine)],
    creategif=true,
    pathname="/tmp/animationtest.gif")
```
