**ImageProjectiveGeometry**

コンピュータビジョンのための射影幾何学をサポートする関数。

ピーター・コヴェシ

[peterkovesi.com](http://peterkovesi.com)

*Projective*

  * Camera - カメラのパラメータを定義する構造体。
  * cameraproject - 3Dポイントをカメラ画像に投影します。
  * imagept2plane - 画像ポイントを平面に投影し、その3D位置を返します。
  * imagecorners2plane - 画像のコーナーの位置を平面に投影します。
  * imagept2ray - 画像ポイントに対応する視線を計算します。
  * imagept2ray! - 画像ポイントに対応する視線を計算します。
  * camera2projmatrix - Camera構造体からカメラ投影行列を生成します。
  * decomposecamera - カメラ投影行列の分解。
  * rq3 - 3x3行列のRQ分解。
  * makehomogeneous - 非同次座標の配列にスケール1を追加します。
  * makeinhomogeneous - 同次座標を非同次座標に変換します。
  * hnormalise - 同次座標の配列をスケール1に正規化します。
  * hnormalise! - 同次座標をスケール1にインプレースで正規化します。
  * homography1d - 1Dホモグラフィを計算します。
  * homography2d - 2Dホモグラフィを計算します。
  * solveaffine - 2つのセットの2Dポイント間のアフィン変換を解決します。
  * normalise1dpts - 1D同次ポイントを正規化します。
  * normalise2dpts - 2D同次ポイントを正規化します。
  * skew - 3ベクトルから3x3の斜対称行列を構築します。
  * hcross - 同次クロス積、結果はs = 1に正規化されます。
  * fundmatrix - 8点以上から基本行列を計算します。
  * affinefundmatrix - 4点以上からアフィン基本行列を計算します。
  * fundfromcameras - カメラ行列または構造体からの基本行列。
  * stereorectify - ステレオペアの画像を整列します。
  * stereorectifytransforms - 画像ペアをステレオ整列ペアに変換するホモグラフィを計算します。
  * transformedimagebounds - 変換Hによって画像のコーナーが変換される場所を見つけ、境界を返します。
  * imgtrans - 画像の同次変換。
  * imgtrans! - 画像の同次変換。
  * idealimagepts - 歪みのない理想的な画像ポイント。
  * solvestereopt - ステレオポイントの同次線形解。
  * undistortimage - 画像からレンズ歪みを除去します。
  * hline - 同次座標で定義された2D線をプロットします。
  * mapimage2plane! - 3Dの平面に画像を投影します。
  * plotcamera - ポーズを示すカメラのグラフィカルな表現をプロットします。

*Corner Features*

  * shi_tomasi - Shi-Tomasiコーナー検出器。
  * harris - Harrisコーナー検出器。
  * noble - Harrisコーナー検出器のノーブルの変種。
  * coherence - 構造テンソルから画像のコヒーレンスを計算します。
  * structuretensor - 画像上の構造テンソル値を計算します。
  * hessianfeatures  - 画像内のヘッセ行列特徴の行列式を計算します。
  * fastradial - ロイとゼリンスキーの高速放射状特徴検出器。

*RANSAC*

  * ransac - RANSACアルゴリズムを使用してデータにモデルをロバストにフィットさせます。
  * ransacfithomography - RANSACを使用して2Dホモグラフィをフィットさせます。
  * ransacfitfundmatrix - RANSACを使用して基本行列をフィットさせます。
  * ransacfitaffinefundmatrix - RANSACを使用してアフィン基本行列をフィットさせます。
  * ransacfitplane - RANSACを使用して3Dポイントの配列に平面をフィットさせます。
  * ransacfitline - RANSACを使用して3Dポイントの配列に線をフィットさせます。
  * iscolinear - 3つのポイントは共線ですか。
  * fitline2d - 2Dポイントのセットに線を最小二乗法でフィットさせます。
  * fitline3d - 3Dポイントのセットに線をフィットさせます。
  * fitplane - 3つ以上のポイントにフィットした平面の係数を解決します。

*RANSAC demos*

  * fitlinedemo - RANSAC線フィッティングをデモします。
  * fitplanedemo - RANSAC平面フィッティングをデモします。
  * fitfunddemo - 基本行列計算の例。
  * fithomogdemo - ホモグラフィを見つける例。

*Transforms*

  * trans - x、y、zによる同次変換。
  * rotx - x軸周りの回転のための同次変換。
  * roty - y軸周りの回転のための同次変換。
  * rotz - z軸周りの回転のための同次変換。
  * dhtrans - デナビット・ハーテンバーグ行列を計算します。
  * homotrans - ポイント/ラインの同次変換。
  * invht - 同次変換行列の逆。
  * inveuler - オイラー変換の逆。
  * invrpy - ロール・ピッチ・ヨー変換の逆。
  * angleaxis - 角度-軸記述子を構築します。
  * normaliseangleaxis - 角度-軸記述子を正規化します。
  * angleaxisrotate - 角度-軸記述子を使用してベクトルを回転させます。
  * angleaxis2matrix - 角度-軸記述子を4x4の同次変換行列に変換します。
  * matrix2angleandaxis - 同次行列を角度と軸に分解します。
  * matrix2angleaxis - 同次行列を角度-軸記述に変換します。
  * quaternion - クォータニオンを構築します。
  * quaternionconjugate - クォータニオンの共役。
  * quaternionproduct - 2つのクォータニオンの積を計算します。
  * quaternionrotate - クォータニオンによって3Dベクトルを回転させます。
  * quaternion2matrix - クォータニオンを4x4の同次変換行列に変換します。
  * matrix2quaternion - 同次行列をクォータニオンに変換します。
  * vector2quaternion - 3ベクトルをクォータニオン表現に埋め込みます。

*Geometry*

  * ray2raydist - 2つの3Dレイ間の最小距離。
  * circleintersectionpts - 2つの円の交点を見つけます。
  * rectintersect - 長方形が交差するかどうかをテストします。
  * pointinconvexpoly - 2Dポイントが凸多角形内にあるかどうかを判断します。
  * convexpolyintersect - 凸多角形が交差するかどうかをテストします。
  * isconvexpoly - 2D多角形が凸であるかどうかをテストします。

*Utilities*

  * nonmaxsuppts - 特徴/コーナーの非最大抑制。
  * derivative3 - 3タップの離散導関数フィルタ。
  * derivative5 - 5タップの1次および2次離散導関数。
  * derivative7 - 7タップの1次および2次離散導関数。
  * gaussfilt - 便利なガウスフィルタリングのための小さなラッパー関数。
  * dilate1d - 信号の1D形態学的膨張。
  * erode1d - 信号の1D形態学的侵食。
  * imdilate - 画像の形態学的膨張。
  * imerode - 画像の形態学的侵食。
  * circularstruct - 形態学的操作のための円形構造要素を生成します。
  * medfilt2 - 中央フィルタリングのための便利なラッパー。
  * stdfilt2 - 画像全体の局所標準偏差を計算します。
  * floatyx - 2D AbstractImageをy x空間順序の2D浮動小数点配列に変換します。
  * histtruncate - 画像ヒストグラムの端を切り捨てます。
  * imgnormalise/imgnormalize - 画像値を0-1に正規化するか、希望する平均と分散に正規化します。
  * matchbycorrelation - 相関によって画像特徴ポイントをマッチさせます。
  * grey2census - 画像のグレースケール値をセンサス値に変換します。
  * briefcoords - パッチ内のBRIEF記述子サンプリング座標を計算します。
  * grey2lbp - 画像のグレースケール値をローカルバイナリパターンに変換します。
  * grey2lbp! - 画像のグレースケール値をローカルバイナリパターンに変換します。
  * keypause - 続行する前にユーザーがリターンを押すのを待ちます。
