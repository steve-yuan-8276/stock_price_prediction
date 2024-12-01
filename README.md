# Tesla Stock Price Prediction Project

## Overview
This project aims to predict Tesla's stock prices using three different machine learning models: **LSTM**, **RNN**, and **CNN**. The focus is to compare their predictive performance and identify the most suitable approach for accurate stock price forecasting based on minimal input data.

---

## Data Source
The dataset used in this project was retrieved from **Yahoo Finance** via the `yfinance` library. It includes Tesla's historical stock data from **June 29, 2010, to November 25, 2024**, and contains the following two columns:
- **Date**: The date of the stock price record.
- **Adjusted Close Price (adjClose)**: The closing price of Tesla stock adjusted for splits and dividends.

This simplified dataset allows the models to learn directly from the historical price sequence.

---

## Prediction Methods

### 1. **LSTM (Long Short-Term Memory)**
- **Description**: LSTM is a type of recurrent neural network (RNN) designed to handle long-term dependencies in sequential data.
- **Implementation**:
  - Two LSTM layers were stacked to capture temporal patterns.
  - A sliding window of 20 time steps was used to predict the stock price 10 steps ahead.
- **Strength**: Captures long-term trends effectively and produces smooth predictions.
- **Weakness**: Struggles to capture short-term fluctuations and responds slowly to rapid changes.

### 2. **RNN (Recurrent Neural Network)**
- **Description**: A simpler architecture compared to LSTM, designed for sequential data processing.
- **Implementation**:
  - A single RNN layer with 50 units was used.
  - Predictions were made based on the same sliding window approach as LSTM.
- **Strength**: Responds quickly to short-term fluctuations, aligning closely with peaks and troughs.
- **Weakness**: Overfits short-term noise, resulting in more volatile predictions.

### 3. **CNN (Convolutional Neural Network)**
- **Description**: CNN, traditionally used for image data, was adapted here for time-series forecasting.
- **Implementation**:
  - Multiple convolutional layers were used to extract local patterns in the time series.
  - Max pooling was applied to reduce dimensionality, followed by fully connected layers for predictions.
- **Strength**: Captures short-term fluctuations effectively and responds quickly to changes.
- **Weakness**: Overfits short-term noise and lacks robustness for long-term trend forecasting.

---

## Results Analysis

### Comparison of MAPE (Mean Absolute Percentage Error)
The MAPE metric was used to evaluate the performance of the models. Lower MAPE indicates better accuracy.

| Model | MAPE (%) |
|-------|----------|
| **RNN**  | **0.11%** |
| **LSTM** | **0.13%** |
| **CNN**  | **0.16%** |

### Key Observations
1. **RNN** achieved the lowest MAPE, indicating the highest accuracy. It effectively balances short-term responsiveness and long-term trend prediction but risks slight overfitting to noise.
2. **LSTM** performed moderately, capturing overall trends with smooth predictions but lagging in areas of rapid changes.
3. **CNN** had the highest MAPE due to overfitting short-term fluctuations, making it less reliable for consistent long-term trends.

---

## Conclusion

1. **Best Model**: The RNN model outperformed LSTM and CNN in terms of accuracy and balance between short- and long-term forecasting.
2. **Use Case Recommendations**:
   - **RNN**: Suitable for applications requiring both short-term accuracy and long-term trend reliability.
   - **LSTM**: Ideal for long-term trend forecasting with smoother predictions.
   - **CNN**: Best for high-frequency trading or scenarios where short-term fluctuations dominate.

---

## Future Improvements
1. **Feature Engineering**: Introduce additional features such as trading volume or macroeconomic indicators to improve predictive performance.
2. **Hybrid Models**: Combine the strengths of LSTM, RNN, and CNN in a single hybrid architecture to better capture both long-term trends and short-term fluctuations.
3. **Alternative Data Sources**: Incorporate external data such as financial news or market sentiment to enhance accuracy.
4. **Fine-Tuning**: Optimize hyperparameters for each model to achieve better performance.

---

## Acknowledgments
Special thanks to **Yahoo Finance** for providing the historical stock price data and to the open-source community for supporting libraries like `TensorFlow`, `Keras`, and `Matplotlib`, which made this project possible.
