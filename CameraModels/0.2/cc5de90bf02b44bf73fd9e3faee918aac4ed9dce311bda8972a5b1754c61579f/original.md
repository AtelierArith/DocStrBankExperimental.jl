```julia
struct CameraCalibration{R<:Real, N} <: CameraModels.AbstractCameraModel
```

Standard pinhole camera model with distortion parameters (aka camera intrinsics).  

Notes:

  * Image origin assumed as top-left.
  * Keeping with Images.jl,

      * width of the image are matrix columns from left to right.
      * height of the image are matrix rows from top to bottom.
      * E.g. `mat[i,j] == img[h,w] == mat[h,w] == img[i,j]`

          * This is to leverage the unified Julia Arrays infrastructure, incl vectors, view, Static, CPU, GPU, etc.

## Legacy Comments:

Pinhole Camera model is the most simplistic.

Notes

  * https://en.wikipedia.org/wiki/Pinhole_camera
  * Standard Julia *[Images.jl](https://juliaimages.org/latest/)-frame* convention is, `size(img) <==> (i,j) <==> (height,width) <==> (y,x)`,

      * Common *camera-frame* in computer vision and robotics, `(x,y) <==> (width,height) <==> (j,i)`,
      * Using top left corner of image as `(0,0)` in all cases.
      * Direct comparison with [OpenCV convention](https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html) is:

          * `(x,y) [CamXYZ] <==> (j,i) [Images.jl] <==> (u,v) [OpenCV]` – look very carfully at `(u,v) <==> (j,i)` in *image-frame*
  * Always follow right hand rule for everything.
  * An abstract type [`AbstractCameraModel`](@ref) is provided to develop implementations against `struct` and `mutable struct` types.

DevNotes

  * https://en.wikipedia.org/wiki/Distortion_(optics)

Also see: [`AbstractCameraModel`](@ref) [`CameraCalibrationMutable`](@ref), (TODO: `ProjectiveCameraModel`)
