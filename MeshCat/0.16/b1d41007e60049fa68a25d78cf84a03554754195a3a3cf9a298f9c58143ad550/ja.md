```
vis = Visualizer()
```

新しい MeshCat ビジュアライザーインスタンスを構築します。

便利なメソッド：

```
vis[:group1] # シーンのサブツリーを表す新しいビジュアライザーを取得
setobject!(vis, geometry) # このビジュアライザーのシーンのサブツリーに表示されるオブジェクトを設定
settransform!(vis, tform) # このビジュアライザーのシーンのサブツリーの変換を設定
setvisible!(vis, false) # シーンのこの部分を非表示にする
```
