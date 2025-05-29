```
scale(d::AbstractNMRData)
```

Return a scaling factor for the data combining the number of scans, receiver gain, and, if specified, the sample concentration.

$$
\mathrm{scale} = \mathrm{ns} \cdot \mathrm{rg} \cdot \mathrm{conc}
$$
