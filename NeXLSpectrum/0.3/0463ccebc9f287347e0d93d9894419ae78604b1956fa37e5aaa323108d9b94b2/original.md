fittedcontinuum(     spec::Spectrum,     det::EDSDetector,     resp::AbstractArray{<:Real,2}; #     mode = :Global [ | :Local ] # Fit to all ROIs simultaneously (:Global) or to each roi independently (:Local)     minE::Float64 = 1.5e3,     maxE::Float64 = 0.95 * spec[:BeamEnergy],     width::Int = 20, # Width of ROI at each end of each patch of continuum that is matched     brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,     mc::Type{<:MatrixCorrection} = Riveros1993,   )::Spectrum

Fit the continuum under the characteristic peaks by fitting the closest continuum ROIs.  The low energy peaks are fit using the continuum immediately higher in energy and the high energy peaks are fit using the continuum on both sides.

  * mode = :Global [ | :Local ] Global fits the model to the data using a single scale factor. :Local tweaks the

global model at ROIs above and below the characteristic peaks.

Typically, :Global produces the overall best fit but :Local fits better around the characteristic peaks and is    better for modeling the continuum under the peaks.
