# TCM-CTCM
Temporal coherence mapping and cross-regional temporal coherence mapping (cross-time functional connectivity).
Please cite the following papers:

1. Resting state fMRI-based temporal coherence mapping, https://arxiv.org/abs/2109.00146                                                                          
2. Cross-time functional connectivity analysis,  https://arxiv.org/abs/2109.00518

Usage: 

       tcm -d 30 -r 0.3 -c 30 -m brainmask.nii.gz -i datfile.nii.gz -o tcmfilename.nii.gz
       d -- length of the embedding window
       r -- cut off for the correlation coefficient. correlation coefficient between two embedding vectors will be set to be 0 if the absolute is <=r
       c -- number of cpu cores to be used
       m --  brain mask used to remove nonbrain voxels
       i -- input data
       o --  output file name
There will be 8 maps in the output: pcc, ncc, pcc/ncc, rr_bin, rr_bin/nrr_bin, tot_sum_pseglen, tot_sum_nseglen, tot_sum_pseglen/tot_sum_nseglen.
       pcc -- mean positive cc
       ncc -- mean negative cc
       rr_bin -- mean rate of the thresholded positive cc.
       nrr_bin -- mean rate of the thresholded negative cc.
       tot_sum_pseglen -- sum of the line segment of the thresholded positive cc matrix diagonals
       tot_sum_nseglen -- sum of the line segment of the thresholded negative cc matrix diagonals
       
       ctcm -d 30 -r 0.3 -c 30 -roi roiimg.nii.gz -m brainmask.nii.gz -i datfile.nii.gz -o ctcmfilename.nii.gz
       d -- length of the embedding window
       r -- cut off for the correlation coefficient. correlation coefficient between two embedding vectors will be set to be 0 if the absolute is <=r
       c -- number of cpu cores to be used
       roi -- seed file name
       m --  brain mask used to remove nonbrain voxels
       i -- input data
       o --  output file name

There will be 10 maps in the output: pcc*100, ncc*100, pcc_md*100, ncc_md*100, max_avg_diagcc, loc_max_avg_diagcc, max_diagmean_len_pcc, loc_max_diagmean_len_pcc, sum_len_pcc, sum_len_ncc.
       pcc -- mean positive cc
       ncc -- mean negative cc
       pcc_md -- mean postive cc in the main diagonal 
       ncc_md -- mean negative cc in the main diagonal 
       max_avg_diagcc -- maximal mean diagonal cc
       max_avg_diagcc -- location of the diagonal where the maximal mean diagonal cc locates
       max_diagmean_len_pcc -- maximal mean diagonal line segment length
       loc_max_diagmean_len_pcc -- location of the diagonal where max_diagmean_len_pcc locates
       sum_len_pcc -- sum of the line segment of the binarized positive cross correlation matrix
       sum_len_ncc -- sum of the line segment of the binarized negative cross correlation matrix
