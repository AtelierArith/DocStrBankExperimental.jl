```
least_occurence_threshold(w, d, p; confidence = 0.95)
```

Computes the least number of occurences that a motif has to have in order not to be considered a product of chance. input:     ts : input time-series     w : motif size (window size).     d : # of allowed errors between motifs.     confidence (optional) : the level of desired confidence. If  set to 0.5, the expected number of motifs chains matching         'match*number' times by chance will be 0.5. (defaults to 0.5) Returns:     match*number : match number by chance allowed by 'confidence'.
