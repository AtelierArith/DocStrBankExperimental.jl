```
run_tesseract(image, extra_args...; kwargs...) -> String
```

メモリ内の画像に対してTesseractを実行し、結果を`String`として取得する関数です。エラー/警告は`Logging`を通じて報告されるため、例外はスローされません。

# 引数

  * `image`: `Images`モジュールと互換性のある形式の処理対象画像。
  * `extra_args::String...`: 出力の性質を変更するためのオプション引数（例: [`"tsv"`](https://tesseract-ocr.github.io/tessdoc/Command-Line-Usage.html)）

# キーワード

  * `lang::Union{String, Nothing}` Tesseractで設定する言語（オプション）
  * `psm::Integer`: ページセグメンテーションモード（PSM）:

      * `psm=0`:   方向とスクリプトの検出（OSD）のみ。
      * `psm=1`:   OSDを伴う自動ページセグメンテーション。
      * `psm=2`:   OSDやOCRなしの自動ページセグメンテーション。
      * `psm=3`:   OSDなしの完全自動ページセグメンテーション。（デフォルト）
      * `psm=4`:   変動サイズのテキストの単一列を仮定。
      * `psm=5`:   垂直に整列したテキストの単一均一ブロックを仮定。
      * `psm=6`:   単一均一テキストブロックを仮定。
      * `psm=7`:   画像を単一のテキスト行として扱う。
      * `psm=8`:   画像を単一の単語として扱う。
      * `psm=9`:   画像を円の中の単一の単語として扱う。
      * `psm=10`:  画像を単一の文字として扱う。
      * `psm=11`:  スパーステキスト。特に順序を問わず、できるだけ多くのテキストを見つける。
      * `psm=12`:  OSDを伴うスパーステキスト。
      * `psm=13`:  生の行。Tesseract特有のハックをバイパスして、画像を単一のテキスト行として扱う。
  * `oem::Integer`: OCRエンジンモード（OEM）:

      * `oem=0`:   レガシーエンジンのみ。
      * `oem=1`:   ニューラルネットLSTMエンジンのみ。（デフォルト）
      * `oem=2`:   レガシー + LSTMエンジン。
      * `oem=3`:   デフォルト、利用可能なものに基づく。
  * `kwargs`: Tesseractコマンドに"-c"設定変数として送信される他のキーと値のペア。オプションは`tesseract --print-parameters`で確認できます。

# 戻り値

  * `String`: 抽出されたテキスト、またはエラーが発生した場合は空の文字列

# 例

```julia-repl
julia> using Images;
julia> using OCReract;
julia> img_path = "/path/to/img.png";
julia> img = load(img_path);
julia> res_text = run_tesseract(img, psm=3, oem=1);
julia> println(strip(res_text));
```
