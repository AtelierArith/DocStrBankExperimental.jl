OCReractは、よく知られたOCRエンジンであるTesseractのシンプルなJuliaラッパーです。

ここでは、使用例の簡単な例を示します：

# 例

```julia-repl
julia> using Images
julia> using OCReract
julia> img_path = "/path/to/img.png";
# ディスク上
julia> run_tesseract(img_path, "/tmp/res.txt", psm=3, oem=1)
# メモリ上
julia> img = load(img_path);
julia> res_text = run_tesseract(img, psm=3, oem=1);
julia> println(strip(res_text));
```

詳細については、https://github.com/leferrad/OCReract.jlのホームページを確認してください。
