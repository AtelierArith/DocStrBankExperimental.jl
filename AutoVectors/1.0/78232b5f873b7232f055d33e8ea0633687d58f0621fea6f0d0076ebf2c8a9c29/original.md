```
fast(v::AutoVector,i)
```

fast(v,i) is like accessing v[i], but without the check for being outside the logical range.  If i is outside, fast  may or may not throw a standard range exception depending on whether i lands outside the data vector's range. For use when i is known to be inside the logical range.  Combined with @inbounds, there will be no range checking at all, for optimal speed.
