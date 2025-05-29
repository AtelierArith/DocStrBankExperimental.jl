```
  item(args...; kwargs...)
```

---

### 引数

---

1. コンテンツ

      * `tag::String` - レンダリングするHTMLタグ; 提案: `checkbox`/`radio`/`toggle`をカプセル化する際には'ラベル'を使用することで、ユーザーがアイテム全体をクリック/タップすると、前述のコンポーネントのモデル変更がトリガーされます。例: `a` `label` `div`
      * `insetlevel::Int` - インセットを適用; アバター/左側が欠けているが、他のアイテムとコンテンツを左側に揃えたい場合や、メニューを構築している場合に便利です。例: `insetlevel!="1"`
2. 一般

      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値; 例: `0` `100`
3. ナビゲーション

      * `href::String` - ネイティブ<a>リンクのhref属性; 'to'/'exact'/'replace'プロパティより優先されます。例: `http://genieframework.com`
      * `target::String` - ネイティブ<a>リンクのtarget属性; 'href'プロパティと一緒にのみ使用; 'to'/'exact'/'replace'プロパティより優先されます。例: `_blank` `_self` `_parent` `_top`
4. 状態

      * `disable::Bool` - コンポーネントを無効モードにする
      * `active::Bool` - アイテムを'アクティブ'状態にする
      * `clickable::Bool` - `item`はクリック可能ですか？もしそうであれば、ホバー効果を追加し、'click'イベントを発生させます
      * `manualfocus::Bool` - アイテムを手動フォーカス状態にする; アイテムがフォーカスされているかどうかを決定する'focused'プロパティを有効にし、ネイティブのホバー/フォーカス状態に依存しません
      * `focused::Bool` - フォーカス状態を決定します。'manual-focus'が有効/trueに設定されている場合のみ
5. スタイル

      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知する
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
