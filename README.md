# OpenCV_Study

## ch1_Prac

import cv2
import sys

```python
# 이미지 파일을 불러옵니다.
img = cv2.imread('cat.bmp')
# flags=cv2.IMREAD_GRAYSCALE
if img is None:
	print('img is none')
	sys.exit()
else:
	# namedWindow에 cv2.normalresize를 인자로 넣어주면 이미지창을
    # resize 할 수 있다.
	cv2.namedWindow('image')
	cv2.imshow('image', img)
	# 흑백 사진으로 저장
	# imshow 와 waitkey를 같이 써야 이미지를 볼 수 있다.
    # 불러온 이미지를 새로운 이미지파일로 저장할 수 있다.
	cv2.imwrite('catgray.jpg', img)
	cv2.waitKey()
	# cv2.destroyWindow는 window의 이름을 받아 창을 닫는다.
	cv2.destroyAllWindows()
```

### how to read file?
a=cv2.imread('cat.bmp')

if a is None:
    print('no image')
    sys.exit()
    
### To save as another type

cv2.imwrite('cat__.png',a)

cv2.namedWindow('catimage',cv2.WINDOW_NORMAL)
cv2.imshow('catimage',a)
cv2.waitKey()

cv2.destroyAllWindows()




import matplotlib.pyplot as plt

BGRimg=cv2.imread('cat.bmp')
RGBimg=cv2.cvtColor(BGRimg,cv2.COLOR_BGR2RGB)

plt.axis('off')
plt.imshow(RGBimg)
plt.show()

Grayimg=cv2.imread('cat.bmp',cv2.IMREAD_GRAYSCALE)
plt.axis('off')
plt.imshow(Grayimg,cmap='gray') #colormap=gray
plt.show()

plt.subplot(121),plt.imshow(RGBimg),plt.axis('off')
plt.subplot(122),plt.imshow(Grayimg,cmap='gray'),plt.axis('off')
plt.show()

import glob

img_list=glob.glob('.\\images\\*.jpg')

if not img_list:
    print('NO images')
    sys.exit()

cv2.namedWindow('images',cv2.WINDOW_NORMAL)
cv2.setWindowProperty('images', cv2.WND_PROP_FULLSCREEN, cv2.WINDOW_FULLSCREEN);

cnt=len(img_list)
print(cnt)
idx=0

while True:
    img=cv2.imread(img_list[idx])

    if img is None:
        print('there''s  no images')
        break
    
    cv2.imshow('images',img)
    if cv2.waitKey(1000)>=0:
        break

    idx+=1
    if idx>=cnt:
        idx=0

cv2.destroyWindow('images')


    

