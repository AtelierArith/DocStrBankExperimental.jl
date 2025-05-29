```julia
calcCalibResidualAprilTags!(
    images,
    allTags;
    tagList,
    taglength,
    VERT,
    HORI,
    f_width,
    f_height,
    c_width,
    c_height,
    s,
    boardPattern,
    dodraw
)

```

Grid of AprilTags calibration helper function.  This function sets up a squared cost to be minimized  by any method, including `Optim.opimize`.  The cost function is constructed by assuming a grid of 40 AprilTags are of equal size and on a common co-planar surface like a computer screen.  

The cost function is constructed by predicting from each tag detection individually where the corners of all  other 39 tags should be on the co-planar surface.  The discrepanc_height between the predicted and detected tag  positions are square accumulated. 

### Notes

  * Assume regular spacing grid of 40 AprilTags 36h11, ids=1:40,

      * down 1:5 by 8 columns 1:5:40 across where taglength and spacing gap are equal.
      * See grid file at AprilTags/data/CameraCalibration/AprilTagGrid1to40.png
  * Current implementation requires all 40 tags to be visible and detected

      * Contributions welcome to allow a few missed detections.
  * Take pictures of the grid with the camera you want to calibrate, making sure all tags are clearly visible.

      * Combinations of the grid nearer and further, centered and slanted around the edges of the field of view are best.
      * Any number of images can be used, the more the better.
      * Note that half a doen high-res images might take up to 20 mins or so to optimize.
  * Julia Images.jl follows the common ``::Array` column-major–-i.e. vertical-major–-index convention

      * That is `img[vertical, horizontal]`
      * See https://evizero.github.io/Augmentor.jl/images/#Vertical-Major-vs-Horizontal-Major-1
  * This function has the ability to draw the predicted tag corners, see keyword `dodraw=true`.
  * This is not a copy of any other AprilCal or such software, this was newly written code out of pure frustration when getting stuff to work.  The more native Julia code the better, because Julia is much more mobile and versatile than any of the other calibration software out there.  See DevNotes below for roadmap of features to add,  contributions welcome.

### Example

Also see `AprilTags/examples/AprilTagsGridClibration.jl`.

This example shows how a series of photos of the tag grid image (just use your computer screen, not a projector)  can be used to calibrate a camera.  This example only shows the basic pinhole parameters, although more are possible,  see keyword arguments for which calibration parameters are available.  The latter part shows how to draw crosses to see before and after result.  

```julia
using AprilTags
using FileIO

# where are the photos of the calibration files
filepaths = ["photo1.jpg"; "photo2.jpg";...]
# load the images into memory
imgs = load.(filepaths)

# It's imporant that you measure and specify the tag length correctly here
# 30 mm is just a guess, insert your own correct tag measurements here.
taglength = 0.03

# rough guess of what calibration parameters might be
# img[rows,columns] <==> img[height, width]
c_width = size(imgs[1],2) / 2 # columns across in Images.jl
c_height = size(imgs[1],1) / 2 # rows down in Images.jl
f_width = size(imgs[1],1)
f_height=f_width

#  detect the tags and duplicate the memory before freeing the detector
detector = AprilTagDetector()
tags = detector.(imgs) .|> deepcopy
# remember to free detector later

# setup the cost function, you can add more parameters here if you like
obj = (f_width, f_height, c_width, c_height) -> calcCalibResidualAprilTags!( imgs, tags, taglength=taglength, f_width=f_width, f_height=f_height, c_width=c_width, c_height=c_height, dodraw=false )
obj_ = (fc_wh) -> obj(fc_wh...)

# check that it works
obj_([f_width, f_height, c_width, c_height])

## Bring in the Optim.jl optimization routines
using Optim

# Run the optimization. BFGS is slower by more precise, it's okay to mix and match as coarse and fine optimization stages
result = optimize(obj_, [f_width; f_height; c_width; c_height], BFGS(), Optim.Options(x_tol=1e-8))

# see the optimized calibration parameters
@show f_width_, f_height_, c_width_, c_height_ = (result.minimizer...,)

## show the before and after images to visually confirm things are working
using ImageView

# bad calibration
img1_before = deepcopy(imgs[1])
calcCornerProjectionsAprilTags!(img1_before, taglength=taglength, f_width=f_width, f_height=f_height, c_width=c_width, c_height=c_height, dodraw=true)
imshow(img1_before)

# new calibration
img1_after = deepcopy(imgs[1])
calcCornerProjectionsAprilTags!(img1_after, taglength=taglength, f_width=f_width_, f_height=f_height_, c_width=c_width_, c_height=c_height_, dodraw=true)
imshow(img1_after)

# free the detector memory
freeDetector!(detector) # could also use a deepcopy to duplicate the memory to a secondary location and free the primary immediately
```

### DevNotes

  * FIXME common JuliaRobotics/CameraModels.jl package shoudl be made
  * TODO Radial distortion parameters should be added, see https://en.wikipedia.org/wiki/Distortion_(optics)
  * TODO allow missed detections on grid of 40 tags
  * TODO auto-detect the grid so that any grid can be used (still assuming regular spacing)

### Related

[`calcCornerProjectionsAprilTags!`](@ref)
