```
stepper(fieldname::Symbol, args...; kwargs...)
```

---

# 例アプリ

---

```julia-repl
@app begin
  @in step = 1
end

ui() = [
    htmldiv(class = "q-pa-md",
        stepper(:step, ref = "stepper", color = "primary", animated = "", [
            StippleUI.step(name = R"1", title = "キャンペーン設定の選択", icon = "settings", done = R"step > 1", 
                """
                作成する各広告キャンペーンについて、クリックやコンバージョンに対して支払う意欲がある金額、広告を表示したいネットワークや地理的な場所などを制御できます。
                """
            ),
            StippleUI.step(name = R"2", title = "広告グループの作成", caption = "オプション", icon = "create_new_folder", done = R"step > 2",
                "広告グループには、共有のキーワードセットをターゲットにする1つ以上の広告が含まれます。"
            ),
            StippleUI.step(name = R"3", title = "広告テンプレート", icon = "assignment", disable = "", 
                "このステップは無効になっているため表示されません。"
            ),
            StippleUI.step(name = R"4", title = "広告の作成", icon = "add_comment",
                """
                さまざまな広告テキストを試して、最も多くの顧客を引き付けるものを見つけ、広告拡張機能などを使用して広告を強化する方法を学びます。広告に問題が発生した場合は、広告が実行されているかどうかを確認し、承認の問題を解決する方法を見つけてください。
                """
            ),
            template(var"v-slot:navigation" = "",
                steppernavigation([
                    btn(R"step === 4 ? '完了' : '続行'", @click("$refs.stepper.next()"), color = "primary", ),
                    btn("戻る", @if("step > 1"), flat = "", color = "primary", @click("$refs.stepper.previous()"), class = "q-ml-sm", )
                ])
            )
        ])
    )
]

ui()

@page("/", ui)

up()
```

---

### 引数

---

1. 動作

      * `keep-alive::Boolean` - コンテンツに対してVueのネイティブ<keep-alive>コンポーネントを使用するのと同等
      * `keep-alive-include::String | Array | RegExpv1.15+` - <keep-alive>のためのVueのネイティブincludeプロパティを使用するのと同等; 値は有効なVueコンポーネント名でなければなりません

        例: `"a,b"`, `"/a|b/"`, `['a', 'b']`
      * `keep-alive-exclude::String | Array | RegExpv1.15+` - <keep-alive>のためのVueのネイティブexcludeプロパティを使用するのと同等; 値は有効なVueコンポーネント名でなければなりません

        例: `"a,b"`, `"/a|b/"`, `['a', 'b']`
      * `keep-alive-max::Number` - <keep-alive>のためのVueのネイティブmaxプロパティを使用するのと同等

        例: `2`
      * `animated::Boolean` - パネル間の遷移を有効にする（'transition-prev'および'transition-next'プロパティも参照）
      * `infinite::Boolean` - コンポーネントを無限に表示する（最後のパネルに達したとき、次のものが最初のものになる）
      * `swipeable::Boolean` - スワイプイベントを有効にする（コンテンツのタッチ/マウスイベントに干渉する可能性があります）
      * `vertical::Boolean` - ステッパーを垂直モードにする（デフォルトでは水平）
      * `transition-prev::String` - Quasarの埋め込み遷移の1つ（'animated'プロパティが設定されている場合のみ効果があります）

        デフォルト値: `"slide-right/slide-down"`

        例: `"fade"`, `"slide-down"`
      * `transition-next::String` - Quasarの埋め込み遷移の1つ（'animated'プロパティが設定されている場合のみ効果があります）

        デフォルト値: `"slide-left/slide-up"`

        例: `"fade"`, `"slide-down"`
      * `header-nav::Boolean` - ヘッダーを通じてナビゲーションを許可
      * `contracted::Boolean` - 狭いウィンドウでヘッダーラベルを非表示にする
2. スタイル

      * `dark::Boolean` - コンポーネントに背景が暗い色であることを通知
      * `flat::Boolean` - 'フラット'デザインを適用（デフォルトの影なし）
      * `bordered::Boolean` - コンポーネントにデフォルトの境界線を適用
      * `header-class::String` - ヘッダーに割り当てるクラス定義

        例: `"my-special-class"`
