```
JopNlProp3DAcoIsoDenQ_DEO2_FDTD(; kwargs...)
JopLnProp3DAcoIsoDenQ_DEO2_FDTD(; v, kwargs...)
```

3D粘弾性、等方性、可変密度モデリングのための`Jets`非線形または線形化演算子を作成します。

# モデルパラメータ

この伝播器は、以下の表に示す2つのモデルパラメータで動作します。

| パラメータ | 説明      |
|:-----:|:------- |
|  `v`  | P波速度    |
|  `b`  | 浮力（逆密度） |

速度`v`と浮力`b`は**アクティブ**パラメータであり、ヤコビアン機構を使用して反転することができます。また、**パッシブ**パラメータとして定数であることもできます。パラメータが**アクティブ**である場合、そのモデルに割り当てられるコンポーネントがあります。

モデルは4Dで、モデルパラメータの最も遅い次元です。地球モデルのプロパティは、`state(F).active_modelset`辞書を介して遅い次元の配列インデックスにマッピングされます。

# 例

## モデルと取得幾何学の設定

1. Jets、WaveFD、およびJetPackWaveFDモジュールをロードします。
2. モデルの離散化、座標サイズ、および間隔を設定します。
3. 取得幾何学を設定します。これには、時間の離散化、ソースとレシーバーの位置、およびソースウェーブレットが含まれます。
4. 定数浮力配列を作成します。

```
using Jets, WaveFD, JetPackWaveFD
nz,ny,nx = 100, 80, 60                        # 空間離散化サイズ
dz,dy,dx = 20.0, 20.0, 20.0                   # 空間離散化サンプリング
ntrec = 1101                                  # 記録データの時間サンプル数
dtrec = 0.0100                                # 記録データのサンプルレート
dtmod = 0.0025                                # モデリングデータのサンプルレート
wavelet = WaveletCausalRicker(f=5.0)          # 使用するウェーブレットのタイプ（ソース署名）
sz = dz                                       # ソースZ位置
sy = dy*(ny/2)                                # ソースY位置
sx = dx*(nx/2)                                # ソースX位置
rz = [dz for iy = 1:ny, ix = 1:nx][:];        # 受信機Y位置の配列
ry = [(iy-1)*dy for iy = 1:ny, ix = 1:nx][:]; # 受信機Y位置の配列
rx = [(ix-1)*dx for iy = 1:ny, ix=1:nx][:];   # 受信機X位置の配列
b = ones(Float32, nz, ny, nx);                # 浮力モデル（逆密度）
```

## 非線形演算子の構築と適用

1. 非線形演算子`F`を作成します。
2. 定数速度モデルm₀を作成します。
3. 定数速度モデル`m₀`を使用して非線形前方モデリングを実行し、結果のモデリングデータを`d`に返します。

```
F = JopNlProp3DAcoIsoDenQ_DEO2_FDTD(; b = b, isinterior=true, nsponge = 10, ntrec = ntrec, 
    dz = dz, dy = dy, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sy = sy, sx = sx, rz = rz, ry = ry, rx = rx)
m₀ = 1500 .* ones(domain(F));
d = F*m₀;              # 前方非線形演算子
```

## 線形化ヤコビアン演算子の構築と適用（メソッド1）

1. ジェットの構築によって非線形演算子`F`を直接作成します。
2. 定数速度モデルm₀を作成します。
3. 点`m₀`での`F`の線形化によってヤコビアン演算子`J`を作成します。
4. ランダムモデル摂動ベクトル`δm`を作成します。
5. モデル摂動ベクトル`δm`に対して線形化前方（ボーン）モデリングを実行し、結果のデータ摂動を`δd`に返します。
6. データ摂動ベクトル`δd`に対して線形化随伴（ボーン）移行を実行し、結果のモデル摂動を`δm`に返します。

ヤコビアン演算子`J`と`J'`は、シリアライズされた非線形前方波場を必要とし、これは必要に応じて自動的に生成されます。この例からの標準出力へのログを監視すると、最初に非線形前方の有限差分進化が表示され、その後に線形化前方、最後に線形化随伴が表示されます。

```
F = JopNlProp3DAcoIsoDenQ_DEO2_FDTD(; b = b, isinterior=true, nsponge = 10, ntrec = ntrec, 
    dz = dz, dy = dy, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sy = sy, sx = sx, rz = rz, ry = ry, rx = rx)
m₀ = 1500 .* ones(domain(F));
J = jacobian(F, m₀)
δm = rand(domain(J));
δd = J*δm;             # 前方線形化演算子
δm = J'*δd;            # 随伴線形化演算子
```

## 線形化ヤコビアン演算子の構築と適用（メソッド2）

1. 定数速度モデルm₀を作成します。
2. ジェットの構築によって点`m₀`でのヤコビアン演算子`J`を直接作成します。
3. ランダムモデル摂動ベクトル`δm`を作成します。
4. モデル摂動ベクトル`δm`に対して線形化前方（ボーン）モデリングを実行し、結果のデータ摂動を`δd`に返します。
5. データ摂動ベクトル`δd`に対して線形化随伴（ボーン）移行を実行し、結果のモデル摂動を`δm`に返します。

```
m₀ = 1500 .* ones(Float32, nz, ny, nx);       # 速度モデル
J = JopLnProp3DAcoIsoDenQ_DEO2_FDTD(; v = m₀, b = b, isinterior=true, nsponge = 10, ntrec = ntrec, 
    dz = dz, dy = dy, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sy = sy, sx = sx, ry = ry, rz = rz, rx = rx)
δm = rand(domain(J));
δd = J*δm;             # 前方線形化演算子
δm = J'*δd;            # 随伴線形化演算子
```

# 必要なパラメータ

  * `v` ジェットが線形化される点。この引数は`JopLnProp3DAcoIsoDenQ_DEO2_FDTD`のコンストラクタで必要ですが、`JopNlProp3DAcoIsoDenQ_DEO2_FDTD`では必要ありません。このコンストラクタは上記の最後の例に示されています。
  * `dtmod` モデリングデータのサンプルレート。モデリングサンプルレートの下限を次の式で確立できます：`dt = 0.75 * 0.38 * max(dx,dz) / maximum(v)`。通常のコーラン–フリードリッヒス–ルーウィ条件（CFL条件）は、有限差分モデリングの安定性のために修正され、粘弾性実装の影響を含むため、サンプルレートは25%小さくする必要があります。
  * `dtrec` 記録データの時間サンプル数。`dtrec`が`dtmod`の偶数倍である必要があることに注意してください。
  * `ntrec` 記録データの時間サンプル数。モデリングデータのサンプル数は`ntrec`、`dtrec`、および`dtmod`から決定されます。

# オプションのパラメータ

引数のデフォルトは角括弧内に示されています。

  * `b [ones(Float32,0,0,0)]` 浮力（逆密度）配列。
  * `srcfieldfile [joinpath(tempdir(), "field-4e129a56-7cf3-4f2e-b7c8-ea288b4b7ef2.bin")]` 圧縮された非線形ソース波場のシリアル化に使用されるスクラッチファイルへのフルパス。
  * `comptype [nothing]` 非線形ソース波場のシリアル化に使用する圧縮のタイプ。圧縮のタイプは次のいずれかでなければなりません：

      * `nothing` - 圧縮なし。
      * `Float32` - 波場が`Float64`の場合、Float32への単純な変換を行います。
      * `UInt32` - CvxCompressを使用した圧縮（ウィンドウ処理 + 2Dウェーブレット変換 + 閾値処理 + 量子化 + ランレングスエンコーディング）。
  * `compscale [1e-2]` 非線形ソース波場のシリアル化前の圧縮のための閾値を決定します。大きな値はより攻撃的な圧縮を意味します。ヤコビアン操作からの出力に違いが見え始める前に、compscaleを1.0に増やすことができるでしょう。
  * `nz_subcube, ny_subcube, nx_subcube [32]` 非線形ソース波場の圧縮に使用されるウィンドウのZ、Y、およびXサイズ。`[8 <= n*_subcube <=256]`の要件に注意してください。
  * `isinterior [false]` 非線形ソース波場がどのように保存されるかを示すブールフラグ。大きなモデルの場合、`isinterior = true`で操作が速くなりますが、線形化の正確性テストが失敗する可能性があります。

      * `true` 吸収境界を含むモデル全体がシリアル化およびデシリアル化されます。
      * `false` 吸収境界を除くモデルの内部部分がシリアル化およびデシリアル化されます。
  * `sz [0.0]` ソースZ座標の配列。複数のソースが提供される場合、有限差分進化中に同時に注入されます。
  * `sy [0.0]` ソースY座標の配列。
  * `sx [0.0]` ソースX座標の配列。
  * `st [0.0]` ソース遅延時間の配列。
  * `interpmethod [:hicks]` ソースとレシーバーのための物理的補間のタイプ。物理グリッド座標上にない位置に対して、情報を注入または抽出するために補間が使用されます。`interpmethod`は次のいずれかでなければなりません：

      * `:hicks` ヒックス3Dシンク補間（各位置あたり最大8x8x8の非ゼロ点）
      * `:linear` バイリニア補間（各位置あたり最大2x2x2の非ゼロ点）
  * `rz [[0.0]]` 受信機Z座標の2D配列
  * `ry [[0.0]]` 受信機Y座標の2D配列
  * `rx [[0.0]]` 受信機Z座標の2D配列
  * `z0 [0.0]` Z次元の物理座標の原点。
  * `y0 [0.0]` Y次元の物理座標の原点。
  * `x0 [0.0]` X次元の物理座標の原点。
  * `dz [10.0]` Z次元の物理座標の間隔。
  * `dy [10.0]` Y次元の物理座標の間隔。
  * `dx [10.0]` X次元の物理座標の間隔。
  * `freqQ [5.0]` マクスウェル体近似による減衰のみの中心周波数。減衰モデルに関する詳細は`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `qMin [0.1]` 減衰のみのマクスウェル体近似に使用されるモデルの境界でのQpの最小値。この値はQpにとって物理的に意味のある値ではなく、減衰を使用して吸収境界条件を実装し、計算領域の境界での外向き波を排除します。減衰モデルに関する詳細は`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `qInterior [100.0]` 減衰のみのマクスウェル体近似に使用されるモデルの内部でのQpの値。この値は吸収境界から離れたQpの物理的に意味のある値です。減衰モデルに関する詳細は`JetPackWaveFD`パッケージのドキュメントを参照してください。
  * `padz, pady, padx [0.0], [0.0], [0.0]` - `Ginsu`で決定されたアパーチャに追加のパディングを適用します。詳細は`Ginsu`を参照してください。
  * `nbz_cache, nby_cache, nbx_cache [512], [8], [8]` Z、X、Y次元のキャッシュブロックのサイズ。一般に、Z（高速）次元のキャッシュブロックはその次元の全体サイズ以上であるべきであり、遅い次元のキャッシュブロックサイズは一般に小さく、全体のブロックがキャッシュに収まるようにします。
  * `nsponge [50]` 吸収境界に使用するグリッドセルの数。高忠実度モデリングの場合、これは> 60グリッドポイントであるべきですが、低周波数の全波形反転などのいくつかの使用ケースではかなり小さくすることができます。
  * `wavelet [WaveletCausalRicker(f=5.0)]` ソースウェーブレットは、ウェーブレットタイプまたは配列として指定できます。
  * `freesurface [false]` 自由表面（`true`）または吸収（`false`）の上部境界条件が適用されるかどうかを決定します。
  * `imgcondition` ["standard"] 使用されるイメージング条件のタイプを選択します。"standard"、"FWI"、および"RTM"から選択します。"FWI"と"RTM"は、イメージング条件の前にKz波数フィルタリングを実行し、長波長を促進（FWI用）したり、長波長の逆散乱エネルギーを除去（RTM用）します。"MIX"は、パラメータRTM_weightを使用してFWIイメージング条件を混合します。現在、真の随伴は"standard"イメージング条件にのみ存在します。
  * `RTM_weight [0.5]` イメージング条件における短波長と長波長のバランスを決定します。値0.0はFWIイメージング条件に相当し、値0.5は標準イメージング条件に相当し、値1.0はRTMイメージング条件に相当します。
  * `nthreads [Sys.CPU_THREADS]` モデリングのOpenMP並列化に使用するスレッドの数。
  * `reportinterval [500]` 伝播に関する情報がログされる間隔。

参照：`Ginsu`、`WaveletSine`、`WaveletRicker`、`WaveletMinPhaseRicker`、`WaveletDerivRicker`、`WaveletCausalRicker`、`WaveletOrmsby`、`WaveletMinPhaseOrmsby`
