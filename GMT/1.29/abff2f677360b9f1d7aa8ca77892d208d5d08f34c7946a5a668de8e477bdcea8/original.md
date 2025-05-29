```
D = mat2ds(D::GMTdataset, inds::Tuple) -> GMTdataset
```

Cut a GMTdataset D with the indices in INDS but updating the colnames and the Timecol info. INDS is a Tuple of 2 with ranges in rows and columns. Ex: (:, 1:3) or (:, [1,4,7]), etc... Attention, if original had attributes other than 'Timeinfo' there is no guarentie that they remain correct. 
