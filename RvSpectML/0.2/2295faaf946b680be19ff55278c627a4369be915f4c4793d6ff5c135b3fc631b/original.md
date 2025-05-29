bin*times*consecutive( times, n ) Computes mean times from conseuctive bins of n times (to go with bin*consecutive*spectra). Returns floor(length(times)/n) elements.

WARNING:  Simply takes consecutive times, so some bins may be from spectra that weren't taken close together. TODO:  Create version that pays attention to timestamps.
