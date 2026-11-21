
# DeepSubDAS Dataset Metadata Investigation

## 1. Dataset Identification

- Dataset name: DeepSubDAS
- Dataset type: Submarine Distributed Acoustic Sensing (DAS)
- Publisher: Zenodo
- Dataset DOI: 10.5281/zenodo.16014744
- Official record: https://zenodo.org/records/16014744
- Associated publication: https://doi.org/10.1093/gji/ggag061
- Data format: HDF5

The dataset contains submarine DAS seismic recordings and corresponding manually or semi-automatically labelled earthquake phase information.

Its primary research purpose is earthquake P- and S-wave phase picking.

## 2. Our Downloaded Pilot File

Filename:

20211102T152000_patch1_highnoise_30_100_0_100.h5

Local path:

data/raw/deepsubdas/

File size: 33,602,048 bytes

Official MD5:

3b1bbbeb9358b9e93dbd764d8acb4cc5

Local checksum was previously verified against the official Zenodo checksum.

## 3. Directly Observed HDF5 Structure

The HDF5 file contains two root datasets:

- patch
- mask

### Patch

- Shape: (300, 4000)
- Data type: float32
- Number of channels: 300
- Number of samples per channel: 4000

### Mask

- Shape: (3, 300, 4000)
- Data type: float64
- Number of annotation layers: 3

The three mask layers sum to approximately 1 at every channel-sample position.

No useful root or dataset attributes specifying sampling frequency, channel spacing, or physical units were found during the initial inspection.

## 4. Information Reported in the Associated Research Paper

The published DeepSubDAS research paper reports the following training-data preparation procedures:

- Waveforms were bandpass-filtered between 1 and 20 Hz.
- Waveforms were resampled to a uniform sampling rate of 100 Hz.
- Original DAS channel spacing was preserved.
- Forty-second waveform segments were extracted.
- Training patches contained approximately 200 to 500 DAS channels.
- Earthquake records containing both P and S phases were selected.
- Real DAS noise was added to earthquake data to improve robustness under different SNR conditions.

These statements describe the research paper's training-data preparation methodology.

They should not automatically be treated as independently verified metadata for every individual HDF5 file.

## 5. Comparison with Our Pilot File

Our file contains 300 channels, which is within the 200–500 channel range reported by the paper.

It also contains 4000 samples.

If the reported 100 Hz sampling rate applies to this particular file:

4000 samples / 100 samples per second = 40 seconds.

This agrees with the 40-second segment duration described in the paper.

However, the sampling rate and duration of this individual file have not yet been independently verified from file-level metadata.

## 6. Metadata Still Requiring Verification

The following information remains unresolved:

1. Exact sampling frequency of the individual HDF5 recording.
2. Exact physical channel spacing.
3. Gauge length.
4. Physical measurement units.
5. Original acquisition and processing history of this particular patch.
6. Exact ordering of the three HDF5 annotation layers.

These values must not be invented or assumed.

## 7. Annotation Classes

The associated research paper describes a three-class output consisting of:

- P-wave
- S-wave
- Noise

However, the exact mapping between these classes and mask indices 0, 1, and 2 in our downloaded HDF5 file has not yet been verified.

The mask layers will therefore remain identified by numerical index until the original annotation convention is confirmed.

## 8. Research Implications

The pilot recording provides a useful starting point for real submarine DAS signal analysis.

The paper's reported 100 Hz sampling rate and 40-second segments are consistent with the dimensions of our pilot recording, but file-specific verification is still required.

The distinction between submarine and land-based DAS recordings must also be maintained when developing and evaluating detection methods.

## 9. References

1. Xiao et al., DeepSubDAS: An Earthquake Phase Picker from Submarine Distributed Acoustic Sensing Data.

   https://doi.org/10.1093/gji/ggag061

2. Official DeepSubDAS dataset, Zenodo.

   https://doi.org/10.5281/zenodo.16014744

3. DeepSubDAS supplementary implementation and model resources, Zenodo.

   https://zenodo.org/records/19002976

## 10. Current Status

Literature-based metadata investigation initiated.

File-level sampling frequency, spatial calibration, physical units, and annotation index ordering remain unresolved.

No original research data has been modified.
