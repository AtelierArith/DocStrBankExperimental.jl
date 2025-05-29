predict_smooth(qr::QNN, z::AbstractVector, bw::AbstractVector)

Predict a quantile at the point z for the fitted model qr.  The vector bw contains bandwidths, which can either be the same length of z (a bandwidth for each variable), or a vector of length 1 (the same bandwidth for all variables).
