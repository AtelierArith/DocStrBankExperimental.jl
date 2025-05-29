```
movie(main; pre=nothing, post=nothing, kwargs...)
```

アニメーションシーケンスと映画を作成します。

完全なGMT（`GMT.jl`のものではない）ドキュメントは[`movie`](http://docs.generic-mapping-tools.org/latest/movie.html)を参照してください。

## パラメータ

  * **main** :: [Type => Str]

    フレーム依存のプロットを作成するスタンドアロンのGMT.jlスクリプトの名前。``
  * **C** | **canvas** :: [Type => Str]

    映画のフレームを構成する際に使用されるキャンバスサイズを指定します。   (http://docs.generic-mapping-tools.org/latest/movie.html#c)
  * **N** | **name** :: [Type => Str]

    フレーム画像と最終映画ファイルを含むサブディレクトリの名前を決定します。   (http://docs.generic-mapping-tools.org/latest/movie.html#n)
  * **T** | **frames** :: [Type => Int | Str]

    生成する画像フレームの数を指定するか、フレームごとに1レコードのパラメータセットを含むファイルを提供します。    (http://docs.generic-mapping-tools.org/latest/movie.html#t)
  * **pre** :: [Type => Str]

    オプションの*backgroundscript*ファイル（GMT.jlスクリプト）は、1つまたは2つの目的で使用できます：（1）映画を作成するためにmainscriptが必要とするファイル（timefileなど）を作成することができ、（2）すべてのフレームの背景を形成する静的背景プロットを作成することができます。   (http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **post** :: [Type => Str]

    オプションの*foregroundscript*ファイル（GMT.jlスクリプト）は、すべてのフレームに重ねる静的前景プロットを作成するために使用できます。    (http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **A** | **gif** :: [Type => Str]		$Args = [+l[n]][+sstride]$

    アニメーションGIFファイルを作成します。映画が何度も再生されるべきかどうかを指定し、再生回数を追加できます。   (http://docs.generic-mapping-tools.org/latest/movie.html#a)
  * **D** | **frame_rate** :: [Type => Int]

    最終アニメーションの表示フレームレートをフレーム毎秒で設定します [24]。   (http://docs.generic-mapping-tools.org/latest/movie.html#d)
  * **E** | **titlepage** :: [Type => Str | tuple]

    映画の静的タイトルページを作成するタイトルページスクリプトを指定します [タイトルなし]。    (http://docs.generic-mapping-tools.org/latest/movie.html#e)
  * **F** | **format** :: [Type => Str]	$Arg = format[+ooptions]$

    最終的なビデオ製品のフォーマットを設定します。mp4（MPEG-4映画）またはwebm（WebM映画）を選択します。   (http://docs.generic-mapping-tools.org/latest/movie.html#f)
  * **G** | **fill** :: [Type => Str | Int | Touple]

    プロットが開始される前にキャンバスの色または塗りつぶしを設定します [なし]。   (http://docs.generic-mapping-tools.org/latest/movie.html#g)
  * **H** | **scale** :: [Type => Number]

    有効なドット毎単位を一時的に増加させ、フレームをラスタライズし、最後に同じ因子で画像をダウンサンプリングします。   (http://docs.generic-mapping-tools.org/latest/movie.html#h)
  * **I** | **includefile** :: [Type => Str]

    includefileの内容をすべての映画スクリプトがアクセスするmovie_initスクリプトに挿入します。   (http://docs.generic-mapping-tools.org/latest/movie.html#i)
  * **K** | **fading** :: [Type => Number | Str | Tuple]	$Arg = [+f[i|o]fade[s]][+gfill][+p] ]$

    メインアニメーションシーケンスのフェードインおよびフェードアウトを追加します [フェードなし]。   (http://docs.generic-mapping-tools.org/latest/movie.html#k)
  * **L** | **label** :: [Type => Str]

    個々のフレームの自動ラベリング。   (http://docs.generic-mapping-tools.org/latest/movie.html#l)
  * **M** | **cover_page** :: [Type => number]	$Arg = frame[,format]$

    カバーページ用の単一フレームを選択します。このフレームは現在のディレクトリに書き込まれます。   (http://docs.generic-mapping-tools.org/latest/movie.html#m)
  * **P** | **progress** :: [Type => Str | Tuple]

    進行状況インジケーターの自動配置。   (http://docs.generic-mapping-tools.org/latest/movie.html#p)
  * **Q** | **debug** :: [Type => Bool | Str]		$Arg = [s]$

    デバッグ：作成したすべてのファイルとディレクトリを検査のために残します。   (http://docs.generic-mapping-tools.org/latest/movie.html#q)
  * **Sb** | **background** :: [Type => Str | Function]

    オプションの背景スクリプトまたはbg PSファイル [GMT6.1のみ](http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **Sf** | **foreground** :: [Type => Str | Function]

    オプションの前景スクリプトまたはfg PSファイル [GMT6.1のみ](http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **W** | **work_dir** :: [Type => Str]

    デフォルトでは、すべての一時ファイルとフレームPNGファイルは**name**で設定されたサブディレクトリプレフィックスに構築されます。相対または完全なディレクトリパスとして別のworkdirを指定することで上書きできます。   (http://docs.generic-mapping-tools.org/latest/movie.html#w)
  * **Z** | **clean** :: [Type => Bool]

    最終映画を組み立てた後、**name**ディレクトリ全体を消去します [デフォルトではすべての画像を含むディレクトリを残します。   (http://docs.generic-mapping-tools.org/latest/movie.html#z)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

```
