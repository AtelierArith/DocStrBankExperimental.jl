```
intentplot(ibn::IBN)
intentplot!(ax, ibn::IBN)
```

`ibn`のグラフプロットを作成します。

## 属性

  * `show_routers = false`: ノードのラベルを表示します
  * `show_links = false`: リンクのラベルを表示します。
  * `subnetwork_view = false`: コントローラビューのインデックスでノードラベルを表示します。
  * `intentidx = nothing`: 渡されたインテントをハイライトします。
