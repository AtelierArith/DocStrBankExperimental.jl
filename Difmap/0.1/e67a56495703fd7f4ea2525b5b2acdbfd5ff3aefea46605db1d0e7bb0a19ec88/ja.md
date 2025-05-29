# 概要

[difmap](ftp://ftp.astro.caltech.edu/pub/difmap/) プログラムのための Julia ラッパー。difmap スクリプトを便利に実行し、入出力ファイルやログを処理します。`difmap_jll.jl` パッケージに依存して `difmap` バイナリを提供します。

# 使用法

プロットを含む [Pluto ノートブック](https://aplavin.github.io/Difmap.jl/test/examples.html) も参照してください。

```jldoctest mylabel
julia> using Difmap

julia> script = [
          "print(1 + 2)",
          "exit",
       ];

julia> res = Difmap.execute(script);

julia> res.success
true

julia> Difmap.inout_pairs(res)[begin+1:end-1]  # 最初と最後の行には現在の時間が含まれています
1-element Vector{Pair{String, Vector{String}}}:
 "print(1 + 2)" => ["3"]
```

```jldoctest mylabel
julia> script = [
           "observe vis.fits",
           "select I",
           "mapsize 512, 0.2",
           "clean 500",
           "restore",
           "device tmp.ps/PS",
           "mapplot cln",
           "save result",
           "exit",
       ];


julia> vis_file = joinpath(dirname(dirname(pathof(Difmap))), "test/data/vis.fits");

julia> res = Difmap.execute(script,
           in_files=[vis_file => "vis.fits"],
           out_files=["result.fits", "result.mod", "result.par", "result.uvf", "tmp.ps"] .=> nothing,  # 目標は何もない - これらのファイルは無視します
       );

julia> res.success
true

julia> Difmap.inout_pairs(res)[begin+1:end-1]  # 最初と最後の行には現在の時間が含まれています
8-element Vector{Pair{String, Vector{String}}}:
 "observe vis.fits" => ["UV FITS ファイルを読み込み中: vis.fits", "AN テーブル 1: 36 の可能なベースラインのうち 4 つの統合。", "見かけのサンプリング: 1 visibilities/baseline/integration-bin。", "ソースを発見: J0000+0248", "", "8 つの IF があり、合計 8 チャンネル:", "", "IF  チャンネル    周波数  周波数オフセット  チャンネル数   全体の IF", "原点での原点  チャンネルごと   チャンネル数    帯域幅", "------------------------------------------------------------- (Hz)"  …  "05        5    4.416e+09      3.2e+07          1      3.2e+07", "06        6    4.512e+09      3.2e+07          1      3.2e+07", "07        7    4.544e+09      3.2e+07          1      3.2e+07", "08        8    4.576e+09      3.2e+07          1      3.2e+07", "", "偏波: RR", "", "履歴の行を 0 行読み込みました。", "", "1152 visibilities を読み込み中。"]
         "select I" => ["偏波 I は利用できません。", "偏波を選択中: RR,  チャンネル: 1..8", "IF 1 チャンネルを読み込み中: 1..1", "IF 2 チャンネルを読み込み中: 2..2", "IF 3 チャンネルを読み込み中: 3..3", "IF 4 チャンネルを読み込み中: 4..4", "IF 5 チャンネルを読み込み中: 5..5", "IF 6 チャンネルを読み込み中: 6..6", "IF 7 チャンネルを読み込み中: 7..7", "IF 8 チャンネルを読み込み中: 8..8"]
 "mapsize 512, 0.2" => ["マップグリッド = 512x512 ピクセル、セルサイズ 0.200x0.200 ミリ秒。"]
        "clean 500" => ["マップとビームを反転中", "推定ビーム: bmin=1.195 mas, bmaj=3.79 mas, bpa=-3.012 度", "推定ノイズ=0.541101 mJy/ビーム。", "clean: niter=500  gain=0.05  cutoff=0", "コンポーネント: 050  -  クリーンされた合計フラックス = 0.0188812 Jy", "コンポーネント: 100  -  クリーンされた合計フラックス = 0.0252178 Jy", "コンポーネント: 150  -  クリーンされた合計フラックス = 0.0277823 Jy", "コンポーネント: 200  -  クリーンされた合計フラックス = 0.0290343 Jy", "コンポーネント: 250  -  クリーンされた合計フラックス = 0.0300524 Jy", "コンポーネント: 300  -  クリーンされた合計フラックス = 0.0302839 Jy", "コンポーネント: 350  -  クリーンされた合計フラックス = 0.0304884 Jy", "コンポーネント: 400  -  クリーンされた合計フラックス = 0.0304353 Jy", "コンポーネント: 450  -  クリーンされた合計フラックス = 0.0305383 Jy", "コンポーネント: 500  -  クリーンされた合計フラックス = 0.030393 Jy", "500 コンポーネントで差し引かれた合計フラックス = 0.030393 Jy", "クリーン残差 min=-0.000455 max=0.000452 Jy/ビーム", "クリーン残差平均=0.000001 rms=0.000189 Jy/ビーム", "最新のモデルと確立されたモデルの合計フラックス = 0.030393 Jy"]
          "restore" => ["restore: 最後の 'invert' からのビームの推定値を代入中。", "ビームを使って復元中: 1.195 x 3.79 で -3.012 度 (北から東へ)", "クリーンマップ  min=-0.0010866  max=0.019272 Jy/ビーム"]
 "device tmp.ps/PS" => ["デバイスを開こうとしています: 'tmp.ps/PS'"]
      "mapplot cln" => []
      "save result" => ["UV FITS ファイルを書き込み中: result.uvf", "174 モデルコンポーネントをファイルに書き込み中: result.mod", "174 モデルコンポーネントを UV 平面モデルに追加中。", "確立されたモデルには現在 174 コンポーネントと 0.030393 Jy が含まれています", "マップを反転中", "restore: 最後の 'invert' からのビームの推定値を代入中。", "ビームを使って復元中: 1.195 x 3.79 で -3.012 度 (北から東へ)", "クリーンマップ  min=-0.0010295  max=0.019271 Jy/ビーム", "クリーンマップを FITS ファイルに書き込み中: result.fits", "difmap 環境を: result.par に書き込み中"]
```
