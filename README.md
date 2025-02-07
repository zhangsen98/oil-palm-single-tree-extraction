# Oil palm single tree extraction methods:
This repository provides a set of tools for oil palm single tree extraction image processing, focusing on oil palm detection and refinement results. It includes three core detection methods:

1.Gradient Difference Window Detection

2.Double Ring Sliding Detection

3.Adaptive Iterative Erosion Algorithm

Each component performs different image processing tasks, ranging from gradient-based filtering to iterative morphological operations for refining raster data.

# Table of Contents
1. Gradient Difference Window Detection
2. Double Ring Sliding Detection
3. Adaptive Iterative Erosion Algorithm
4. Requirements
# 1. Gradient Difference Window Detection
This method detects significant differences between pixel values within a sliding window. It applies a gradient difference comparison, checking if the gradient exceeds a certain threshold (C), and then processes the results using a sliding window.

# Key Functions:
sliding(): Applies a sliding window operation on the array, summing values within each window.

raster_info(): Retrieves metadata information (e.g., CRS, width, height) from a raster file.
# Parameters:
win_size: The size of the sliding window.

C: Constant threshold for gradient difference.

path: Path to the raster file.

L_path: Path for raster array conversion.

# 2. Double Ring Sliding Detection
This method detects changes using a double ring sliding window, where a large window computes an overall sum, and a smaller window detects local changes. The results are then processed using morphological operations and adaptive thresholding.

# Key Functions:
cv2.getStructuringElement(): Generates structuring elements for morphological operations.

cv2.morphologyEx(): Applies the top-hat transformation to the image.

cv2.threshold(): Applies Otsu’s thresholding to the image.
# Parameters:
A, B, C, D, E, F: Adjustable parameters controlling the detection process, including structuring element size and thresholding values.

S, G, P, M, N: Window sizes and other parameters for processing.

step, X, Y: Parameters controlling the iteration steps over the image.

# 3. Adaptive Iterative Erosion Algorithm
This method refines raster data by applying adaptive erosion iteratively. It removes small areas based on user-defined area thresholds and applies erosion operations using a morphological kernel.

# Key Functions:
array_to_gdf(): Converts a raster array into a GeoDataFrame for vector processing.

gdf_to_array(): Converts a GeoDataFrame back to a raster array.

cv2.erode(): Applies erosion to the raster data.

# Parameters:
max_area, min_area: Thresholds for filtering vector polygons based on area size.

raster_tree_num: Pixel value used to identify trees in the raster data.

iteration_num: Number of iterations for the erosion process.

# 4. Requirements
To run the code, the following libraries are required:

NumPy (for numerical operations)

OpenCV (for morphological operations and image transformations)

GeoPandas (for geospatial data handling)

Rasterio (for raster file reading and metadata extraction)

# Conclusion
This database provides a comprehensive set of tools for oil palm single tree extraction. By combining gradient-based methods, adaptive erosion, and sliding window detection, users can extract meaningful features and perform advanced image analysis.
