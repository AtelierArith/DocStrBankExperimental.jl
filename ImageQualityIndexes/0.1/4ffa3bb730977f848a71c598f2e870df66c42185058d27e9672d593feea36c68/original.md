```
HASLER_AND_SUSSTRUNK_M3 <: NoReferenceIQI
M =  hasler_and_susstrunk_m3(img)
```

Calculates the colorfulness of a natural image using method M3 from [1]. As a guide to interpretation of results, the authors suggest:

| Attribute           |  M3 |
|:------------------- | ---:|
| Not colorful        |   0 |
| slightly colorful   |  15 |
| moderately colorful |  33 |
| averagely colorful  |  45 |
| quite colorful      |  59 |
| highly colorful     |  82 |
| extremely colorful  | 109 |

[1] Hasler, D. and Süsstrunk, S.E., 2003, June. Measuring colorfulness in natural images. In Human vision and electronic imaging VIII (Vol. 5007, pp. 87-96). International Society for Optics and Photonics.
