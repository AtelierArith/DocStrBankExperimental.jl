```
video(args...; kwargs...)
```

`video`コンポーネントを使用すると、Youtubeのようなビデオを簡単に埋め込むことができます。また、デフォルトでコンテナに合わせてサイズが変更されます。

---

### 例

---

### モデル

```julia-repl
julia> @vars RadioModel begin
         v_ratio::R{String} = "16/9"
       end
```

### ビュー

```julia-repl
julia> video(src="https://www.youtube.com/embed/dQw4w9WgXcQ") 
julia> video(ratio=:v_ratio, src="https://www.youtube.com/embed/k3_tw44QsZQ?rel=0")
```

---

### 引数

---

1. アクセシビリティ

      * `title::String` - (アクセシビリティ) 使用される内部iframeのネイティブ'title'属性値を設定します
2. 挙動

      * `fetchpriority::String` - iframeドキュメントを取得する際の相対的な優先度のヒントを提供します。デフォルト: `"auto"` | 受け入れられる値: `"auto"`, `"high"`, `"low"`
      * `loading::String` - ブラウザがiframeをどのように読み込むべきかを示します。デフォルト: `"eager"` | 受け入れられる値: `"eager"`, `"lazy"`
      * `referrerpolicy::String` - フレームのリソースを取得する際に送信するリファラーを示します。デフォルト: `"strict-origin-when-cross-origin"` | 受け入れられる値: `"no-referrer"`, `"no-referrer-when-downgrade"`, `"origin"`, `"origin-when-cross-origin"`, `"origin-when-cross-origin"`, `"strict-origin"`, `"strict-origin-when-cross-origin"`, `"unsafe-url"`
3. モデル

      * `src::String` - iframeに表示するソースURL。
4. スタイル

      * `ratio::Union{String,Int,Float64}` - コンテンツのアスペクト比; 値がStringの場合、計算文（例えば'16/9'）を使用せず、結果のString値を直接指定します（例: '1.7777'）

```
