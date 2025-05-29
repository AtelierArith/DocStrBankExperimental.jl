```
  scrollarea(args...; kwargs...)
```

`scrollarea` コンポーネントは、コンテンツをカプセル化することでスクロールバーをカスタマイズする neat な方法を提供します。これは、`overflow: auto` を持つ DOM 要素のようなもので、ブラウザのデフォルトのスクロールバーの代わりに独自のスタイルのスクロールバーを持ち、いくつかの素晴らしい機能が追加されています。

---

### 例

---

### ビュー

```julia-repl
julia> StippleUI.scrollarea(style="height: 200px; max-width: 300px;", [
          Html.div("Stippleは、純粋なJuliaでインタラクティブなデータアプリケーションを構築するためのリアクティブUIライブラリです。サーバー側ではGenie.jlを使用し、クライアント側ではVue.jsを使用します。Stippleは高性能なMVVMアーキテクチャを使用しており、状態を双方向で自動的に同期させます（サーバー -> クライアントおよびクライアント -> サーバー）し、ワイヤー上でJSONデータのみを送信します。Stippleパッケージは、GenieのHTML APIをリアクティブコンポーネントで拡張する基本的な通信レイヤーを提供します。")
       ])
```

---

### 引数

---

1. 動作

      * `visible::Bool` - スクロールバーの可視性を手動で制御します; デフォルトのマウスオーバー/リーブ動作をオーバーライドします
      * `delay::Union{Int, String}` - コンテンツが変更されると、スクロールバーが表示されます; この遅延は、スクロールバーが再び消えるまでの時間（ミリ秒単位）を定義します（コンポーネントがホバーされていない場合）デフォルトは `1000` 例: `500` `delay!="500`
      * `horizontal::Bool` - getScrollPosition、getScrollPercentage、setScrollPosition、および setScrollPercentage のデフォルトの軸を垂直から水平に変更します（デフォルトは垂直です）
2. 一般

      * `tabindex::Union{Int, String}` - タブインデックスのHTML属性値 `0` `100`
3. スタイル

      * `dark::Bool` - 背景が暗い色であることをコンポーネントに通知します
      * `barstyle::Union{Vector, String, Dict}` - スクロールバー（垂直および水平）のカスタムスタイリングのためのCSSプロパティと値を持つオブジェクト 例: `barstyle!="{ borderRadius: '5px', background: 'red', opacity: 1 }"`
      * `contentstyle::Union{Vector, String, Dict}` - `scrollarea` のコンテナのスタイリングのためのCSSプロパティと値を持つオブジェクト
