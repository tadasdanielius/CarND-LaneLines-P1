First assignment for self driving car

#### Image pre-processing

The image pre-processing works in the same way as was presented during lectures:
* Convert to grayscale
* Apply Canny Edge detector
* Cut region of interested

#### Finding Lines in single frame
* Lines are detected using `cv2.HoughLinesP()`.
* For each detected line slope is calculated.
* Lines are removed if corresponding slope is outside defined range
* Detected lines are split into different sets. One set for left lines and the
other for right line. This I can detect from the slope (negative or positive)

Hopefully selected lines do belong to the right or left line.
Finally I take only points from each line and use [Polynomial
regression](https://en.wikipedia.org/wiki/Polynomial_regression) to find
coefficients $$y=a+bx$$
And that is enough to draw the line.

#### Remarks
The weak part is that I only use 1-degree polynomial, yielding to the line
regression, thus curved lines aren't fitted nicely (optional video). Also,
proper stabilisation mechanism is required to avoid "line jumpings". This could
probably be achieved using [confidence
bands](https://en.wikipedia.org/wiki/Confidence_and_prediction_bands) and if
detected lines doesn't nicely fit in the expected range then use previously
detected line, allowing smooth transitions. <br/>
Further improvemtents could be made by slicing frame into smaller regions and
try to detect lane in each region. <br/>
Optional solution performace at the moment isn't good and further investigation
is required. <br/>
Other weak part is that code needs to be refactored, since most of the stuff are
added to collect data for analysis.<br/>


## Videos

here is processed videos
[Video 1](https://www.facebook.com/tadas.danielius.1/videos/vb.100013501291545/197906807336028/?type=2&theater)
[Video 2](https://www.facebook.com/tadas.danielius.1/videos/vb.100013501291545/197906790669363/?type=2&theater)
[Video 3](https://www.facebook.com/tadas.danielius.1/videos/vb.100013501291545/197906760669366/?type=2&theater)


Full details can be found [here](https://github.com/tadasdanielius/CarND-LaneLines-P1/blob/master/P1%20Solution.ipynb)
