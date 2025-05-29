```
xcorr(x::AbstractVecOrMat{<:Real}, y::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

Returns the cross-correlation of two discrete-time sequences.

If x is a matrix, then r is a matrix whose columns contain the autocorrelation and cross-correlation sequences for all combinations of the columns of x.

---

```
xcorr(x::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

Returns the autocorrelation sequence of x.

Cross-correlation measures the similarity between a vector x and shifted (lagged) copies of a vector y as a function of the lag. 

### Kwargs

  * `demean`: Specifies whether the respective means of x and y should be subtracted from them before  computing their cross correlation.
  * `lags`: When left unspecified and `maxlags=0`, the lags used are the integers from  `-min(size(x,1)-1, 10*log10(size(x,1))) to min(size(x,1), 10*log10(size(x,1)))`
  * `maxlags`: limits the lag range from `-maxlag` to `maxlag`.
