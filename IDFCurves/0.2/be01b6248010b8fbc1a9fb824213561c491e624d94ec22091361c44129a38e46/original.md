plotIDFCurves(model::DependentScalingModel, data::IDFdata; ...)

Plots the IDF curves based on the given model. Pointwise estimations are added (crosses) to illustrate the fitting. Durations and return periods may be chosen by the user but have default values. If show*confidence*intervals = true, 95% confidence intervals associated to the pointwise estimations are represented.
