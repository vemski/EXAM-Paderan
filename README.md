import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          leading: CircleAvatar( 
            backgroundColor: Colors.transparent, 
            radius: 20,
            child: Icon(
              Icons.house,
              color: Colors.white,
            ),
          ),
          title: Text(
            'ListView Builder',
            style: TextStyle(color: Colors.white), // Set the text color to white
          ),
          actions: [
            Padding(
              padding: EdgeInsets.symmetric(horizontal: 17),
            ),
          ],
          backgroundColor: Colors.red,
        ),
        body: Container(
          color: Color(0xFF063970),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Expanded(child: buildListView(['Diovem Paderan', 'Sasuki Uchiha', 'Zoro Roronoa'])),
              ],
            ),
          ),
        ),
      ),
    );
  }

  Widget buildListView(List<String> names) {
    return ListView.separated(
      itemBuilder: (context, position) {
        String name = names[position];
        int letterCount = name.length;

        return Container(
          color: Color(0xFF063970),
          margin: EdgeInsets.symmetric(vertical: 11), // Add vertical margin
          child: Row(
            mainAxisAlignment: MainAxisAlignment.start, // Align horizontally at the start
            crossAxisAlignment: CrossAxisAlignment.center, // Align vertically at the center
            children: [
              Padding(
                padding: const EdgeInsets.symmetric(horizontal: 11), // Add horizontal padding for space
                child: CircleAvatar(
                  backgroundColor: Colors.white, // Set your desired background color
                  radius: 15,
                  // Add your profile image or initials here
                  child: Icon(
                    Icons.person,
                    color: Colors.black,
                  ),
                ),
              ),
              Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text(
                    '$name',
                    style: TextStyle(
                      color: Colors.white,
                      fontSize: 18, // Set your desired font size
                      fontWeight: FontWeight.bold, // Add bold style if desired
                    ),
                  ),
                  Text(
                    '$letterCount Letters',
                    style: TextStyle(color: Colors.white),
                  ),
                ],
              ),
            ],
          ),
        );
      },
      separatorBuilder: (context, position) {
        return SizedBox.shrink();
      },
      itemCount: names.length,
    );
  }
}
