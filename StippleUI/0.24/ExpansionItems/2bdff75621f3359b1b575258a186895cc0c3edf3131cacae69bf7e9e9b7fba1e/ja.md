```
expansionitem(args...; kwargs...)
```

`expansionitem`コンポーネントは、ユーザーにとって即座に関連性のないコンテンツを隠すことを可能にします。クリックすると展開されるアコーディオン要素のように考えてください。また、折りたたみ可能なものとも呼ばれます。

基本的には、追加の機能でラップされた`item`コンポーネントです。したがって、`list`に含めることができ、`item`コンポーネントのプロパティを継承します。

### 例

---

### モデル

```julia-repl
julia> @vars ExpansionModel begin
          dummy::R{Bool} = true
       end
```

### ビュー

```julia-repl
julia> list(bordered=true, class="rounded-borders", [
          expansionitem(expandseparator=true, icon="perm_identity", label="アカウント設定", caption="ジョン・ドー", [
            card([
              cardsection("Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti
              commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste
              eveniet doloribus ullam aliquid.")
            ])
          ]),
          expansionitem(expandseparator=true, icon="signal_wifi_off", label="Wifi設定", [
            card([
              cardsection("Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti
              commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste
              eveniet doloribus ullam aliquid.")
            ])
          ]),
          expansionitem(expandseparator=true, icon="drafts", label="下書き", [
            card([
              cardsection("Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti
              commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste
              eveniet doloribus ullam aliquid.")
            ])
          ])
       ])
```

---

### 引数

---

1. 動作

      * `duration::Int` - アニメーションの持続時間（ミリ秒単位）例: `:duration="1000"`
      * `default-opened::Bool` - 初期レンダリング時に展開アイテムをオープン状態にする; ReactiveModelを使用する場合は上書きされる
      * `expandicontoggle::Bool` - 展開イベントを展開アイコンのみに適用し、ヘッダー全体には適用しない
      * `group::String` - グループに展開アイテムを登録する（そのグループ内のすべての展開アイテムに適用される一意の名前）グループ内でのオープン/クローズ状態を調整するためのもので、いわゆる「アコーディオンモード」例: `my-emails`
      * `popup::Bool` - 展開リストを「ポップアップ」モードにする
2. コンテンツ

      * `icon::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます）例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `expandicon::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます）例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `expandedicon::String` - `expansionitem`が展開されているときの展開アイコン名（Quasarの規約に従う）; 使用すると、展開アイコンの回転アニメーションも無効になります; 'img:'プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `label::Union{String,Symbol}` - ヘッダーラベル
      * `labellines::Union{Int, String}` - 指定された行数で描画するのに十分なスペースがない場合に省略記号を適用する; 1行以上指定された場合、'-webkit-line-clamp' CSSプロパティを使用するため、webkitブラウザでのみ機能します! 例: `labellines="2"` `1` `2`
      * `caption::String` - ヘッダーのサブラベル（'header'スロットを使用しない限り）例: `未読メッセージ: 5`
      * `captionlines::Union{Int, String}` - 指定された行数で描画するのに十分なスペースがない場合に省略記号を適用する; 1行以上指定された場合、'-webkit-line-clamp' CSSプロパティを使用するため、webkitブラウザでのみ機能します! 例: `labellines="2"` `1` `2`
      * `headerinsetlevel::Int` - ヘッダーにインセットを適用する（'header'スロットを使用しない限り）; ヘッダーのアバター/左側が欠けている場合でも、他のアイテムとコンテンツを整列させたい場合や、メニューを構築している場合に便利です例: `headerinsetlevel="1"`
      * `contentinsetlevel::Int` - コンテンツにインセットを適用する（コンテンツのパディングを変更）例: `contentinsetlevel="1"`
      * `expandseparator::Bool` - ヘッダーとコンテンツの間にセパレーターを追加
      * `switchtoggleside::Bool` - 展開アイコンの側を切り替える（デフォルトの「右」から「左」へ）
      * `group::String` - グループに展開アイテムを登録する（そのグループ内のすべての展開アイテムに適用される一意の名前）グループ内でのオープン/クローズ状態を調整するためのもので、いわゆる「アコーディオンモード」例: `my-emails`
3. 状態

      * `disable::Bool` - コンポーネントを無効モードにする
4. スタイル

      * `expand-icon-class::Union{Vector, String, Dict}` - 展開アイコンアイテムセクションにカスタムクラスを適用する例: `text-purple`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知する
      * `dense::Bool` - 密なモード; より少ないスペースを占有
      * `densetoggle::Bool` - 展開アイコンに密なモードを使用
      * `headerstyle::Union{Vector, String, Dict}` - ヘッダーセクションにカスタムスタイルを適用する例: `background: '#ff0000'` `headerstyle=opts( backgroundColor: "#ff0000" )`

```
