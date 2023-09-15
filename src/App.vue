<script setup>
//import
import { ref } from "vue";
//import mountain from "img\puukao.jpg";

//ตัวแปร
const name_Bookers = ref("");
const travel = ref(" ");
const money = ref(0);

//const travellist = ref(['ท่าช้าง','สุขพอดี Simply Happy','RiverSide','Warmup','ตะวันแดง'])
const travellist = ref([
  {name:'WTF Coffee Camp ', price: 80,size:{s: 80, m: 150,l:200},img:"https://gangtravel.com/upload/2022/01/2-7.jpg.webp",text:'ร้านกาแฟริมน้ำตกที่ตกแต่งในสไตล์แคมปปิ้ง   ให้ความรู้สึกเหมือนกำลังนั่งแคมป์ปิ้งกลางป่าเขา'},
  {name:'สุขพอดี Simply Happy',price: 120,size:{s: 120, m: 150,l:200},img:"https://gangtravel.com/upload/2022/01/6-1_800x503.jpg.webp",text:'ร้านคาเฟ่นี้มีที่ตั้งที่เงียบสงบและเป็นธรรมชาติ โดดเด่นด้วยบรรยากาศที่อบอุ่นและน่ารัก'},
  {name:'กำปอ kam Por',price: 150,size:{s: 150, m: 200,l:250},img:"https://gangtravel.com/upload/2022/01/11_800x450-2.jpg.webp",text:'ร้านที่ถูกโอบล้อมด้วยธรรมชาติ ขุนเขา และสายน้ำ บรรยากาศร่มรื่น ตกแต่งน่ารัก อบอุ่น'},
  {name:'ผลิ Phli',price: 120,size:{s: 120, m: 150,l:200},img:"https://www.paiduaykan.com/travel/wp-content/uploads/2022/01/1-SON09405.jpg",text:'ตกแต่งแนวอบอุ่น สไตล์โฮมมี่โดยเอาบ้านไม้สองชั้นมารีโนเวทเป็นคาเฟ่ให้บรรยากาศเหมือน นั่งกินข้าวและจิบกาแฟที่บ้านตัวเอง'},
  {name:'undo studio',price: 150,size:{s: 150, m: 200,l:250},img:"https://www.paiduaykan.com/travel/wp-content/uploads/2020/10/undo-studio1.jpg",text:'คาเฟ่ไซส์มินิที่ดูภาพรวมแล้วน่ารักเหมือนหลุดออกมาจากในการ์ตูน ในส่วนของเมนูมีให้เลือกทั้งชา กาแฟ โกโก้ และขนมเค้กให้ทาน'},
  {name:'yellow cup',price: 100,size:{s: 80, m: 150,l:200},img:"https://www.paiduaykan.com/travel/wp-content/uploads/2020/10/yellow-cup1.jpg",text:'ร้านสีเหลืองละมุนและคุกกี้ช็อกโกแลตหนึบ ๆ หน้าตาน่ารักลอง เป็นการเติมเต็มช่วงเวลาแห่งความสุขได้อย่างเต็มที่'}
]);

const bookinglist = ref([ ]);
const bookings = (destination) => {
  if(destination.numBookings > 0 ){
    bookinglist.value.push({
      name:destination.name,
      bookerName:destination.bookerName,
      bookerphone:destination.bookerphone,
      bookingDate:destination.bookingDatetime,
      text:destination.text
    });
  }
};
//{name:'',table:0,rest_name:''},
//function
function booking(name){
  //name>> + bookinglist
  bookinglist.value.push(name)
  
}
</script>


<template>
  <header>
      <img src="https://cdn-icons-png.flaticon.com/512/553/553966.png" alt="Logo" width="80" height="80" class="d-inline-block align-text-top">
      <p class="fontheader">Coffee Shop Reservation</p>
  </header>
  <div class="p-3 m-0 border-0 bd-example m-0 border-0 ">
  <div class="row align-items-start ">
    <div class="col" v-for="(destination,index) in travellist" :key="index">
      
      <div class="card">
      <img :src="destination.img" class="card-img-top" alt="destination.img" style="height: 250px; width: 300px;">
      <form>
        <div class="card-body">
          <strong class="card-title" style="font-size: 25px;">{{ destination.name }}</strong>
          <p class="font-monospace">Popular Menu: Mint mocha</p>
          <div class="card-text"><span class="font-monospace">Price:{{ destination.price}}</span></div>
          <p>{{ destination.text }}</p>
          
        </div>
        <div class="mb-3">
          <!-- <p>name_Bookers is: {{ name_Bookers }}</p> -->
          <!-- <input v-model="name_Bookers" placeholder="ระบุชื่อผู้จอง" /> -->
          <label for="name_Bookers" class="form-label">ชื่อผู้จอง</label>
          <input type="name" class="form-control" id="name_Bookers" v-model="destination.bookerName" placeholder="โปรดระบุชื่อผู้จอง" >
        </div>
        <div class="mb-3">
          <label for="phone_Bookers" class="form-label">เบอร์โทรศัพศ์</label>
          <input type="name" class="form-control" id="phone_Bookers" v-model="destination.bookerphone" placeholder="โปรดระบุหมายเลขโทรศัพท์ผู้จอง" >
        </div>
        <div>
          <label for="date_Bookers" class="form-lable">วันที่ เวลา</label>
          <input type="datetime-local" class="form-control" id="date_Bookers" v-model="destination.bookingDate">
        </div><br>
        <div>
          <label for="date_Bookers" class="form-lable">จองโต๊ะ</label>
          <input type="number" class="form-control" id="table_Bookers" v-model="destination.numBookings">
          จำกัด 4ท่าน/1โต๊ะ <br>
        </div>
        <a href="#gogo" class="btn btn-primary" @click="booking(destination)">Go to travel</a>
      </form>
        
      </div>
    </div>
    
    
  </div>
</div>

<table class="table" v-if="bookinglist.length>0 " id="gogo">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">list rest</th>
      <th scope="col">Booking</th>
      <th scope="col">Booker Name</th>
      <th scope="col">Phone Number</th>
      <th scope="col">Booking DateTime</th>

    </tr>
  </thead>
  <tbody class="table-group-divider">
    <tr v-for="(booking, index) in bookinglist" :key="index">
      <th scope="row">{{index+1}}</th>
      <td>{{booking.name}}</td>
      <td>{{booking.numBookings}}</td>
      <td>{{booking.bookerName}}</td>
      <td>{{booking.bookerphone}}</td>
      <td>{{booking.bookingDate}}</td>
      <td>{{booking.bookingTime}}</td>
      
    </tr>
  </tbody>
</table>



  <!--div>
    <div v-for="(i,index) in travellist" :key="index">
      {{ index+1 }}
      ชื่อ {{i.name}} ราคา {{ i.price }}
      Size:M = {{ i.size.m }}

      รูป
      แผนที่
    </div>
    
    
    <h1> เธอ ... ไปเที่ยวไหนดี</h1>
    <input type="radio" value="a" v-model="travel"/>ภูเขา 
    <input type="radio" value="b" v-model="travel"/>ทะเล
    <br/>
    <div v-if="travel =='a'"> <img src="img\puukao.jpg" alt="mountain" style="width: 260px;"> </div>
    <div v-else> <img src="img\sea.jpg" alt="sea" style="width: 260px;"></div>
    <div>
      จำนวนเงิน
      <input type="text" v-model="money">
      <div v-if="money < 100">
        อยู่บ้านนอน
      </div>
      <div v-else-if="money >= 100 && money<1000000000">
        ขึ้นรถไปเที่ยว
      </div>
      <div v-else-if="money > 1000000000" >
        ขับเครื่องบินส่วนตัวไป
      </div>
      
    </div>
    <button v-if="money < 50" type="" disabled>go </button>
      <button v-else type="submit">go</button>
  </div!-->

</template>
  
