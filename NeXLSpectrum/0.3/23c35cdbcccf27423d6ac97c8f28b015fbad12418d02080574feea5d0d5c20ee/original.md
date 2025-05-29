```
references(refs::AbstractVector{ReferencePacket}, det::EDSDetector)::FilterFitPacket
references(refs::AbstractVector{ReferencePacket}, fwhm::Float64)::FilterFitPacket
```

Constructs a FilterFitPacket from a vector of `ReferencePackets`.  Each `ReferencePacket` represents a  single ROI for an element.  It is possible more than one `ReferencePacket` might be defined for an  elemental ROI.  In this case, the `ReferencePacket` with the lower index will take preference over later ones.  This allows you to fill in only the missing elemental ROIs using spectra collected from  alternative materials.  For example, a spectrum from F₂Fe is suitable for the Fe K-lines but not the  Fe L-lines. So we might specify F₂Fe first to specify the references for the Fe K-lines and then fill  in the L-lines with a spectrum from pure Fe.
