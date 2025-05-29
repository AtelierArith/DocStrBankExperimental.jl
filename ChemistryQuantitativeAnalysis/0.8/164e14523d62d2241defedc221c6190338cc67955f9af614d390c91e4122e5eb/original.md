```
update_calibration!(batch::Batch{A}, analyte::B) where {A, B <: A}
update_calibration!(batch::Batch, cal_id::Int)
update_calibration!(cal::MultipleCalibration, method::AnalysisMethod)
```

Update calibration obeject for `analyte`, `batch.calibration[cal_id]` or `cal` after modifying any parameters in method or calibration object.
