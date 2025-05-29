```
dashtextareaautocomplete(;kwargs...)
```

DashTextareaAutocompleteコンポーネント。DashTextareaAutocomplete

マルチライン`<textarea>`要素での自動補完を可能にするDash用のシンプルな`@webscopeio/react-textarea-autocomplete`ラッパー。キーワード引数：

  * `id` (String; optional): Dashコールバックでこのコンポーネントを識別するために使用されるID。
  * `className` (String; optional): `<textarea>`のクラス名（`react-textarea-autocomplete`から）。
  * `containerClassName` (String; optional): テキストエリアコンテナのクラス名（`react-textarea-autocomplete`から）。
  * `containerStyle` (Dict; optional): テキストエリアコンテナのスタイル（`react-textarea-autocomplete`から）。
  * `dropdownStyle` (Dict; optional): ドロップダウンラッパーのスタイル。
  * `itemStyle` (Dict; optional): アイテムラッパーのスタイル。
  * `listStyle` (Dict; optional): リストラッパーのスタイル（`react-textarea-autocomplete`から）。
  * `loaderStyle` (Dict; optional): ローダーラッパーのスタイル（`react-textarea-autocomplete`から）。
  * `minChar` (Real; optional): ユーザーが提案をトリガーするために入力すべき文字数。

デフォルトは1です。（`react-textarea-autocomplete`から）

  * `placeholder` (String; optional): `<textarea>`フィールドに何を入力できるかのヒントをユーザーに提供します。
  * `style` (Dict; optional): `<textarea>`のスタイル。（`react-textarea-autocomplete`から）。
  * `triggerChar` (String; optional): 自動補完機構をトリガーする文字。

デフォルトは`:`です。（`react-textarea-autocomplete`から）

  * `value` (String; optional): `<textarea>`に表示される値。
  * `wordList` (Array; required): 自動補完のために利用可能な文字列のリスト。
