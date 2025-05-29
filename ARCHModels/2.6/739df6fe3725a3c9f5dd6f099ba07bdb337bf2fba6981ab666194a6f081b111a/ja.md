```
MultivariateARCHModel(spec::MultivariateVolatilitySpec, data::Matrix;
      			  	  dist=MultivariateStdNormal,
				  	  meanspec::[NoIntercept{T}() for _ in 1:d]
	  			  	  fitted::Bool=false
				  	  )
```

MultivariateARCHModelを作成します。
