<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>নিউ মধুবন দধী এন্ড মিষ্টান্ন ভান্ডার</title>
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --soil-yellow: #F4E285;
            --lite-soil: #FCF5D1;
            --deep-soil: #BC9C22;
            --cream-bg: #FFFEF7;
            --text-brown: #5D4037;
            --soft-border: #E6D5A7;
            --dark-pink: #AD1457;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

        body {
            font-family: 'Hind Siliguri', sans-serif;
            background-color: var(--cream-bg);
            color: var(--text-brown);
            overflow-x: hidden;
        }

        .ripple { position: relative; overflow: hidden; transition: transform 0.1s; }
        .ripple:active { transform: scale(0.95); }

        .full-bg-float {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: url('https://i.ibb.co.com/gb1bMyXJ/image.jpg') center/cover no-repeat;
            z-index: -2; opacity: 0.15; animation: fullUpDown 15s linear infinite;
        }

        @keyframes fullUpDown { 0%, 100% { transform: translateY(-10%); } 50% { transform: translateY(10%); } }

        .hero-header { width: 100%; padding: 50px 20px 30px; background: linear-gradient(to bottom, var(--soil-yellow), transparent); text-align: center; }
        .brand-name { font-size: 26px; font-weight: 900; color: #795548; text-shadow: 1px 1px 2px white; }

        .category-container {
            display: flex; justify-content: center; gap: 10px; padding: 10px;
            overflow-x: auto; white-space: nowrap; position: sticky; top: 0;
            background: var(--cream-bg); z-index: 100; border-bottom: 1px solid var(--soft-border);
        }

        .cat-btn {
            padding: 8px 16px; border-radius: 20px; border: 1px solid var(--deep-soil);
            background: white; color: var(--text-brown); font-weight: bold; font-size: 14px;
        }

        .cat-btn.active { background: var(--dark-pink); color: white; border-color: var(--dark-pink); }

        .coupon-section {
            background: #fff; margin: 10px 15px; padding: 15px; border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05); text-align: center; border: 2px solid var(--soil-yellow);
        }

        .coupon-input { padding: 10px; width: 60%; border: 1.5px solid var(--soft-border); border-radius: 8px; outline: none; }
        .apply-btn { padding: 10px 15px; background: var(--dark-pink); color: white; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; }

        .item-card {
            background: rgba(255, 255, 255, 0.9); margin: 12px 15px; padding: 15px;
            border-radius: 20px; display: flex; align-items: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.03); border: 1px solid var(--soft-border);
        }

        .item-img { width: 85px; height: 85px; border-radius: 15px; background-size: cover; background-position: center; flex-shrink: 0; }
        .item-info { padding-left: 15px; flex: 1; }
        .qty-tag { font-size: 11px; background: #f0f0f0; padding: 2px 8px; border-radius: 10px; color: #666; font-weight: bold; display: inline-block; margin-bottom: 4px; }
        .price-box { font-size: 19px; font-weight: 800; color: #795548; }
        .old-price { font-size: 14px; text-decoration: line-through; color: #999; display: none; margin-right: 5px; }

        .order-now-btn {
            display: inline-block; margin-top: 10px; background: var(--dark-pink);
            color: white; text-decoration: none; padding: 8px 20px;
            border-radius: 50px; font-weight: bold; font-size: 13px;
        }

        .preorder-btn {
            display: block; margin: 20px 15px; background: var(--dark-pink);
            color: white; text-decoration: none; padding: 15px;
            border-radius: 15px; text-align: center; font-weight: bold;
        }

        .map-btn {
            position: fixed; bottom: 100px; right: 20px;
            background: var(--soil-yellow); width: 50px; height: 50px;
            border-radius: 50%; display: flex; justify-content: center; align-items: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2); z-index: 100; border: 1.5px solid var(--deep-soil);
        }

        .floating-wa {
            position: fixed; bottom: 30px; right: 20px;
            background: #25D366; width: 60px; height: 60px;
            border-radius: 50%; display: flex; justify-content: center; align-items: center;
            z-index: 100; box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        footer { background: var(--soil-yellow); padding: 30px 15px; text-align: center; font-weight: bold; margin-top: 20px; }
    </style>
</head>
<body>

    <div class="full-bg-float"></div>

    <div class="hero-header">
        <h1 class="brand-name">নিউ মধুবন দধী এন্ড মিষ্টান্ন ভান্ডার</h1>
        <p>বিশুদ্ধতার অনন্য নাম | প্রতিষ্ঠিত: ২০১১</p>
    </div>

    <div class="category-container">
        <button class="cat-btn ripple active" onclick="filterItems('all', this)">সবগুলো</button>
        <button class="cat-btn ripple" onclick="filterItems('sweet', this)">মিষ্টি</button>
        <button class="cat-btn ripple" onclick="filterItems('yoghurt', this)">দই</button>
        <button class="cat-btn ripple" onclick="filterItems('drink', this)">পানীয়</button>
    </div>

    <div class="coupon-section">
        <input type="text" id="couponCode" class="coupon-input" placeholder="কুপন কোড লিখুন">
        <button class="apply-btn ripple" onclick="applyCoupon()">Apply</button>
        <p id="couponMsg" style="font-size: 12px; margin-top: 5px; font-weight: bold;"></p>
    </div>

    <a href="https://maps.app.goo.gl/VrgzuYJ7EgsJEYbL9?g_st=ac" target="_blank" class="map-btn ripple">
        <svg width="24" height="24" fill="#5D4037" viewBox="0 0 16 16"><path d="M8 16s6-5.686 6-10A6 6 0 0 0 2 6c0 4.314 6 10 6 10zm0-7a3 3 0 1 1 0-6 3 3 0 0 1 0 6z"/></svg>
    </a>

    <div id="itemList">
        <div class="item-card sweet">
            <div class="item-img" style="background-image:url('https://images.unsplash.com/photo-1589119908995-c6837fa14848?w=200')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ৩০ কেজি</span>
                <h3>স্পেশাল রসগোল্লা</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="350">350</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card sweet">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/ZhcK0Yp/rasmalai.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ১৫ কেজি</span>
                <h3>রসমালাই (প্রিমিয়াম)</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="550">550</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card sweet">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/mR0hS6J/kalakand.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ২০ কেজি</span>
                <h3>ক্ষীর কালাকন্দ</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="600">600</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card sweet">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/vH1N7xV/sandesh.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ১০ কেজি</span>
                <h3>স্পেশাল ছানা সন্দেশ</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="700">700</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card yoghurt">
            <div class="item-img" style="background-image:url('https://thumbs.dreamstime.com/b/sweet-curd-mishti-doi-popular-indian-dessert-86221448.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ৪০ কেজি</span>
                <h3>বগুড়ার শাহী দই</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="260">260</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card yoghurt">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/vH1N7xV/sandesh.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ২৫ কেজি</span>
                <h3>সাদা মিষ্টি দই</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="220">220</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card drink">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/m4h8C68/lassi.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ৫০ গ্লাস</span>
                <h3>বাদাম মালাই লাচ্ছি</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="70">70</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>

        <div class="item-card drink">
            <div class="item-img" style="background-image:url('https://i.ibb.co.com/m4h8C68/lassi.jpg')"></div>
            <div class="item-info">
                <span class="qty-tag">মজুত: ৬০ গ্লাস</span>
                <h3>স্পেশাল মালাই ঘোল</h3>
                <div class="price-box"><span class="old-price"></span>৳<span class="base-price" data-price="50">50</span></div>
                <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="order-now-btn ripple">অর্ডার করুন</a>
            </div>
        </div>
    </div>

    <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="preorder-btn ripple">বড় অনুষ্ঠানের জন্য প্রি-অর্ডার</a>

    <footer>
        <p>কবিরাজ কমপ্লেক্স, আক্কেলপুর, জয়পুরহাট</p>
        <p style="font-size: 11px; opacity: 0.7; margin-top: 5px;">© ২০১১-২০২৫ নিউ মধুবন সুইটস</p>
    </footer>

    <a href="https://wa.me/message/UFRZQ4X4BKKBM1" target="_blank" class="floating-wa ripple">
        <svg width="35" height="35" fill="white" viewBox="0 0 16 16"><path d="M13.601 2.326A7.854 7.854 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.06 3.973L0 16l4.104-1.076a7.863 7.863 0 0 0 3.888 1.029h.001c4.368 0 7.926-3.558 7.93-7.93a7.898 7.898 0 0 0-2.322-5.696H13.601zM7.994 14.52a6.573 6.573 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.557 6.557 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592zm3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.007-.247-.007-.38-.007a.729.729 0 0 0-.529.247c-.182.198-.691.677-.691 1.654 0 .977.71 1.916.81 2.049.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.17-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232z"/></svg>
    </a>

    <script>
        function filterItems(category, btn) {
            const items = document.getElementsByClassName('item-card');
            const btns = document.getElementsByClassName('cat-btn');
            for (let b of btns) b.classList.remove('active');
            btn.classList.add('active');
            for (let item of items) {
                if (category === 'all' || item.classList.contains(category)) {
                    item.style.display = 'flex';
                } else {
                    item.style.display = 'none';
                }
            }
        }

        function applyCoupon() {
            const code = document.getElementById('couponCode').value.toUpperCase();
            const msg = document.getElementById('couponMsg');
            const prices = document.getElementsByClassName('base-price');
            const oldPrices = document.getElementsByClassName('old-price');
            let disc = 0;

            if (code === 'RG21') disc = 0.10;
            else if (code === 'RG51') disc = 0.13;
            else if (code === 'RG91') disc = 0.15;
            else {
                msg.style.color = 'red';
                msg.innerText = 'ভুল কুপন কোড!';
                return;
            }

            for (let i = 0; i < prices.length; i++) {
                let base = parseFloat(prices[i].getAttribute('data-price'));
                let newPrice = Math.round(base - (base * disc));
                oldPrices[i].innerText = '৳' + base;
                oldPrices[i].style.display = 'inline';
                prices[i].innerText = newPrice;
            }
            msg.style.color = 'green';
            msg.innerText = (disc * 100) + '% ডিসকাউন্ট যুক্ত হয়েছে!';
        }
    </script>
</body>
</html>
