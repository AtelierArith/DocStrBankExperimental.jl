```
JopNlProp2DAcoTTIDenQ_DEO2_FDTD(; kwargs...)
JopLnProp2DAcoTTIDenQ_DEO2_FDTD(; m₀, kwargs...)
```

2D擬似粘弾性、傾斜横異方性、可変密度モデリングのための`Jets`非線形または線形化演算子を作成します。

# モデルパラメータ

この伝播器は、以下の表に示す5つのモデルパラメータで動作します。

| パラメータ | 説明                    |
|:-----:|:--------------------- |
|  `v`  | P波速度                  |
|  `ϵ`  | 修正トムセンの弱い異方性パラメータ     |
|  `η`  | 修正アルカリファの弱い異方性パラメータ η |
|  `b`  | 浮力（逆密度）               |
|  `θ`  | 垂直からの対称軸の傾斜角（ラジアン）    |

## 擬似粘弾性近似

私たちが採用する擬似粘弾性近似では、自己随伴形式への変換には、せん断波とP波速度の平均比を表すパラメータ`f`と、アルカリファの弱い異方性パラメータ`η`の修正が必要です。これら2つのパラメータの公式を以下に示します。パラメータ`f`は、モデル全体に対してスカラーとして指定され、デフォルト値は0.85であり、これはせん断速度がP波速度の約38%であることを意味します。

  * `η = sqrt[2(ϵ-δ)/(f+2ϵ)]`
  * `f = 1 - Vₛ² / Vₚ²`

私たちが採用する擬似粘弾性近似に関する詳細については、https://library.seg.org/doi/10.1190/segam2016-13878451.1 をご覧ください。

## アクティブおよびパッシブモデルパラメータ

異なるセットの**アクティブ**および**パッシブ**パラメータを定義する2つの動作モードがあります。*速度のみ*と*速度と異方性*です。

**アクティブ**パラメータは、ヤコビアン線形化演算子の機構を使用して反転可能であり、**パッシブ**パラメータは定数です。2つのモードは次のとおりです。

| モード    | アクティブパラメータ      | パッシブパラメータ             |
|:------ |:--------------- |:--------------------- |
| 速度のみ   | [`v`]           | [`ϵ`, `η`, `b`, `θ` ] |
| 速度と異方性 | [`v`, `ϵ`, `η`] | [`b`, `θ` ]           |

パラメータを**パッシブ**にするには、そのパラメータの配列を演算子のコンストラクタに渡します。これは、そのパラメータが状態にあり、演算子の作用によって変化しないことを意味します。コンストラクタに渡されていないパラメータは**アクティブ**であると見なされ、演算子が作用するモデルの一部として、次のインデックスを持つ3D配列として保存されます：`[Z coord][X coord][Active Parameter]`

# 例

## モデルと取得ジオメトリの設定

1. Jets、WaveFD、およびJetPackWaveFDモジュールをロードします。
2. モデルの離散化、座標サイズ、および間隔を設定します。
3. 取得ジオメトリを設定します。これには、時間の離散化、ソースとレシーバーの位置、およびソースウェーブレットが含まれます。
4. `v`、`ϵ`、`η`、`b`、`θ`の定数モデルを作成します。

```
using Jets, WaveFD, JetPackWaveFD
nz,nx = 200, 100                      # 空間離散化サイズ
dz,dx = 20.0, 20.0                    # 空間離散化サンプリング
ntrec = 1101                          # 記録データの時間サンプル数
dtrec = 0.0100                        # 記録データのサンプルレート
dtmod = 0.0025                        # モデリングデータのサンプルレート
wavelet = WaveletCausalRicker(f=5.0)  # 使用するウェーブレットのタイプ（ソースシグネチャ）
sz = dz                               # ソースZ位置
sx = dx*(nx/2)                        # ソースX位置
rx = dx*[0:0.5:nx-1;];                # レシーバーX位置の配列
rz = 2*dz*ones(length(0:0.5:nx-1));   # レシーバーZ位置の配列
b = ones(Float32, nz, nx);            # 定数浮力
ϵ = 0.1 * ones(Float32, nz, nx);      # 定数エプシロン
η = 0.2 * ones(Float32, nz, nx);      # 定数イータ
θ = (π/8) * ones(Float32, nz, nx);    # 定数傾斜角
```

## 非線形演算子の構築と適用（`v`がアクティブ、`ϵ, η, b, θ`がパッシブ）

1. 非線形演算子`F`を作成します。
2. モデルベクトルを作成し、パラメータ`v`を設定します。
3. モデル`m₀`を使用して非線形前方モデリングを実行し、結果のモデリングデータを`d`に返します。

```
F = JopNlProp2DAcoTTIDenQ_DEO2_FDTD(; b = b, ϵ = ϵ, η = η, θ = θ, ntrec = ntrec, dtrec = dtrec, 
    dtmod = dtmod, dz = dz, dx = dx, wavelet = wavelet, sz = sz, sx = sx, rz = rz, rx = rx)
m₀ = zeros(domain(F));
m₀[:,:,1] .= 1500;
d = F*m₀;              # 前方非線形演算
```

## 非線形演算子の構築と適用（`v, ϵ, η`がアクティブ、`b, θ`がパッシブ）

1. 非線形演算子`F`を作成します。
2. モデルベクトルを作成し、パラメータ`v, ϵ, η`を設定します。
3. モデル`m₀`を使用して非線形前方モデリングを実行し、結果のモデリングデータを`d`に返します。

```
F = JopNlProp2DAcoTTIDenQ_DEO2_FDTD(; b = b, θ = θ, ntrec = ntrec, dtrec = dtrec, dtmod = dtmod, 
    dz = dz, dx = dx, wavelet = wavelet, sz = sz, sx = sx, rz = rz, rx = rx)
m₀ = zeros(domain(F));
m₀[:,:,1] .= 1500;
m₀[:,:,2] .= 0.1;
m₀[:,:,3] .= 0.2;
d = F*m₀;              # 前方非線形演算
```

## 線形化ヤコビアン演算子の構築と適用（メソッド1）

この例では、モデル内で`v, ϵ, η`がアクティブパラメータであり、`b, θ`がパッシブであると仮定します。

1. ジェットの構築によって非線形演算子`F`を直接作成します。
2. モデルベクトルを作成し、パラメータ`v, ϵ, η`を設定します。
3. 点`m₀`での`F`の線形化によってヤコビアン演算子`J`を作成します。
4. ランダムモデル摂動ベクトル`δm`を作成します。
5. モデル摂動ベクトル`δm`に対して線形化前方（ボーン）モデリングを実行し、結果のデータ摂動を`δd`に返します。
6. データ摂動ベクトル`δd`に対して線形化随伴（ボーン）移行を実行し、結果のモデル摂動を`δm`に返します。

ヤコビアン演算子`J`と`J'`は、シリアライズされた非線形前方波場を必要とし、これは必要に応じて自動的に生成されます。この例からの標準出力へのログを監視すると、最初に非線形前方の有限差分進化が表示され、その後に線形化前方、最後に線形化随伴が表示されます。

```
F = JopNlProp2DAcoTTIDenQ_DEO2_FDTD(; b = b, θ = θ, ntrec = ntrec, dz = dz, dx = dx, 
    dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, sz = sz, sx = sx, rz = rz, rx = rx)
m₀ = zeros(domain(F));
m₀[:,:,1] .= 1500;
m₀[:,:,2] .= 0.1;
m₀[:,:,3] .= 0.2;
J = jacobian(F, m₀)
δm = rand(domain(J));
δd = J*δm;             # 前方線形化演算
δm = J'*δd;            # 随伴線形化演算
```

## 線形化ヤコビアン演算子の構築と適用（メソッド2）

この例では、モデル内で`v, ϵ, η`がアクティブパラメータであり、`b, θ`がパッシブであると仮定します。

1. モデルベクトルを作成し、パラメータ`v, ϵ, η`を設定します。
2. ジェットの構築によって点`m₀`でヤコビアン演算子`J`を直接作成します。
3. ランダムモデル摂動ベクトル`δm`を作成します。
4. モデル摂動ベクトル`δm`に対して線形化前方（ボーン）モデリングを実行し、結果のデータ摂動を`δd`に返します。
5. データ摂動ベクトル`δd`に対して線形化随伴（ボーン）移行を実行し、結果のモデル摂動を`δm`に返します。

```
m₀ = zeros(Float32, nz, nx, 3);
m₀[:,:,1] .= 1500;
m₀[:,:,2] .= 0.1;
m₀[:,:,3] .= 0.2;
J = JopLnProp2DAcoTTIDenQ_DEO2_FDTD(; m₀ = m₀, b = b, θ = θ, ntrec = ntrec, dz = dz, dx = dx, 
    dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, sz = sz, sx = sx, rz = rz, rx = rx)
δm = rand(domain(J));
δd = J*δm;             # 前方線形化演算
δm = J'*δd;            # 随伴線形化演算
```

# 必要なパラメータ

  * `m₀` ジェットが線形化される点。これは`JopLnProp2DAcoTTIDenQ_DEO2_FDTD`のコンストラクタで必要ですが、`JopNlProp2DAcoTTIDenQ_DEO2_FDTD`では必要ありません。このコンストラクタは上記の最後の例に示されています。どのパラメータがアクティブであり、どれがパッシブであるかを考慮する必要があります。これは上記のモデルパラメータに関する議論と例に基づいています。
  * `dtmod` モデリングデータのサンプルレート。モデリングサンプルレートの下限を次の式で確立できます：`dt = 0.75 * 0.38 * max(dx,dz) / maximum(v)`。通常のコーラン–フリードリッヒス–ルーイ条件（CFL条件）は、有限差分モデリングの安定性のために、擬似粘弾性実装の影響を含めるために*ヒューリスティックに*修正され、25%小さいサンプルレートが必要です。
  * `dtrec` 記録データの時間サンプル数。`dtrec`が`dtmod`の偶数倍である必要があることに注意してください。
  * `ntrec` 記録データの時間サンプル数。モデリングデータのサンプル数は、`ntrec`、`dtrec`、および`dtmod`から決定されます。

# オプションのパラメータ

引数のデフォルトは角括弧内に示されています。

  * `b [ones(Float32,0,0)]` 浮力（逆密度）配列。
  * `θ [zeros(Float32,0,0)]` ラジアンでの対称軸の傾斜角。指定されていない場合はゼロと見なされます。θは浮力`b`と同じサイズの配列である必要があります。
  * `f [0.85]` ここで使用される**擬似粘弾性近似**に関する議論を参照してください。
  * `srcfieldfile [joinpath(tempdir(), "field-96b2aef4-4787-40d8-b888-e9bd4242b309.bin")]` 圧縮された非線形ソース波場のシリアライズに使用されるスクラッチファイルへのフルパス。
  * `comptype [nothing]` 非線形ソース波場のシリアライズに使用する圧縮のタイプ。圧縮のタイプは次のいずれかでなければなりません：

      * `nothing` - 圧縮なし。
      * `Float32` - 波場が`Float64`の場合、Float32への単純な変換を行います。
      * `UInt32` - CvxCompressを使用した圧縮（ウィンドウ処理 + 2Dウェーブレット変換 + 閾値処理 + 量子化 + ランレングスエンコーディング）。
  * `compscale [1e-2]` 非線形ソース波場の圧縮のための閾値を決定します。大きな値はより攻撃的な圧縮を意味します。ヤコビアン操作からの出力に違いが見え始める前に、compscaleを1.0に増やすことができるでしょう。
  * `nz_subcube, nx_subcube [32]` 非線形ソース波場の圧縮に使用されるウィンドウのZおよびXサイズ。`[8 <= n*_subcube <=256]`の要件に注意してください。
  * `isinterior [false]` 非線形ソース波場がどのように保存されるかを示すブールフラグ。大きなモデルの場合、`isinterior = true`の方が操作が速くなりますが、線形化の正確性テストが失敗する可能性があります。

      * `true` 吸収境界を含むモデル全体がシリアライズおよびデシリアライズされます。
      * `false` 吸収境界を除くモデルの内部部分がシリアライズおよびデシリアライズされます。
  * `sz [0.0]` ソースZ座標の配列。複数のソースが提供される場合、有限差分進化中に同時に注入されます。
  * `sx [0.0]` ソースX座標の配列。
  * `st [0.0]` ソース遅延時間の配列。
  * `interpmethod [:hicks]` ソースとレシーバーの物理的補間のタイプ。物理グリッド座標にない位置に対して、情報を注入または抽出するために補間が使用されます。`interpmethod`は次のいずれかでなければなりません：

      * `:hicks` ヒックス2Dシンク補間（各位置につき最大8x8の非ゼロ点）
      * `:linear` バイリニア補間（各位置につき最大2x2の非ゼロ点）
  * `rz [[0.0]]` レシーバーZ座標の2D配列
  * `rx [[0.0]]` レシーバーX座標の2D配列
  * `z0 [0.0]` Z次元の物理座標の原点。
  * `x0 [0.0]` X次元の物理座標の原点。
  * `dz [10.0]` Z次元の物理座標の間隔。
  * `dx [10.0]` X次元の物理座標の間隔。
  * `freqQ [5.0]` 衰退のみの減衰に対するマクスウェル体近似の中心周波数。減衰モデルに関する詳細については、`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `qMin [0.1]` マクスウェル体近似におけるモデルの境界でのQpの最小値。これはQpにとって物理的に意味のある値ではなく、吸収境界条件を実装し、計算領域の境界での外向き波を排除するために減衰を使用します。減衰モデルに関する詳細については、`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `qInterior [100.0]` マクスウェル体近似におけるモデルの内部でのQpの値。これは吸収境界から離れたQpの値であり、物理的に意味のある値です。減衰モデルに関する詳細については、`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `padz, padx [0.0], [0.0]` - `Ginsu`で決定されたアパーチャに追加のパディングを適用します。詳細については`Ginsu`を参照してください。
  * `nbz_cache, nbx_cache [512], [8]` ZおよびX次元のキャッシュブロックのサイズ。一般に、Z（高速）次元のキャッシュブロックはその次元の全体サイズ以上であるべきであり、遅い次元のキャッシュブロックサイズは一般に小さく、全体のブロックがキャッシュに収まるようにします。
  * `nsponge [50]` 吸収境界に使用するグリッドセルの数。高忠実度モデリングの場合、これは> 60グリッドポイントであるべきですが、低周波数の全波形反転などのいくつかの使用ケースではかなり小さくすることができます。
  * `wavelet [WaveletCausalRicker(f=5.0)]` ソースウェーブレット。ウェーブレットタイプまたは配列として指定できます。
  * `freesurface [false]` 自由表面（`true`）または吸収（`false`）の上部境界条件が適用されるかどうかを決定します。
  * `imgcondition` ["standard"] 使用されるイメージング条件のタイプを選択します。"standard"、"FWI"、および"RTM"から選択します。"FWI"および"RTM"は、イメージング条件の前にKz波数フィルタリングを実行し、長波長を促進（FWIの場合）または長波長の逆散乱エネルギーを除去します（RTMの場合）。"MIX"は、パラメータRTM_weightを使用してFWIイメージング条件を混合します。現在、真の随伴は"standard"イメージング条件にのみ存在します。
  * `RTM_weight [0.5]` イメージング条件における短波長と長波長のバランスを決定します。値0.0はFWIイメージング条件に相当し、値0.5は標準イメージング条件に相当し、値1.0はRTMイメージング条件に相当します。
  * `nthreads [Sys.CPU_THREADS]` モデリングのOpenMP並列化に使用するスレッドの数。
  * `reportinterval [500]` 伝播に関する情報がログされる間隔。

参照：`Ginsu`、`WaveletSine`、`WaveletRicker`、`WaveletMinPhaseRicker`、`WaveletDerivRicker`、`WaveletCausalRicker`、`WaveletOrmsby`、`WaveletMinPhaseOrmsby` 
