```julia
struct CameraCalibration{R<:Real, N} <: CameraModels.AbstractCameraModel
```

歪みパラメータ（カメラ内部パラメータとも呼ばれる）を持つ標準的なピンホールカメラモデル。

注意事項：

  * 画像の原点は左上と仮定します。
  * Images.jlに従って、

      * 画像の幅は左から右への行列の列です。
      * 画像の高さは上から下への行列の行です。
      * 例：`mat[i,j] == img[h,w] == mat[h,w] == img[i,j]`

          * これは、ベクトル、ビュー、Static、CPU、GPUなどを含む統一されたJulia配列インフラストラクチャを活用するためです。

## レガシーコメント：

ピンホールカメラモデルは最も単純です。

注意事項

  * https://en.wikipedia.org/wiki/Pinhole_camera
  * 標準的なJulia *[Images.jl](https://juliaimages.org/latest/)-frame* 規約は、`size(img) <==> (i,j) <==> (height,width) <==> (y,x)`、

      * コンピュータビジョンとロボティクスにおける一般的な*カメラフレーム*は、`(x,y) <==> (width,height) <==> (j,i)`、
      * すべての場合において画像の左上隅を`(0,0)`として使用します。
      * [OpenCVの規約](https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html)との直接比較は：

          * `(x,y) [CamXYZ] <==> (j,i) [Images.jl] <==> (u,v) [OpenCV]` – *画像フレーム*における`(u,v) <==> (j,i)`を注意深く見てください。
  * すべてのことに対して右手の法則に従ってください。
  * `struct`および`mutable struct`タイプに対して実装を開発するために、抽象型[`AbstractCameraModel`](@ref)が提供されています。

開発ノート

  * https://en.wikipedia.org/wiki/Distortion_(optics)

また、次も参照してください：[`AbstractCameraModel`](@ref) [`CameraCalibrationMutable`](@ref)、(TODO: `ProjectiveCameraModel`)
